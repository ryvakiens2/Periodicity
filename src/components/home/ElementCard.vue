<template>
    <!-- Class based styling for each element -->
    <div class="element" :style="preloadStyles">
        <div class="atomicnumber">
            {{element.atomicNumber}}
            <span>{{element.atomicMass}}</span>
        </div>
        <div class="symbol">{{element.symbol}}</div>
        <div class="name">{{element.name}}</div>
    </div>
</template>

<script>
export default {
    name: "ElementCard",
    props: ["element"],
    data() {
        return {
            preloadStyles: "opacity: 0"
        };
    },
    mounted: function() {
        setTimeout(() => {
            this.preloadStyles = "opacity: 1";
        }, 500);
    },
    methods: {
        //convert dataset atomic mass to standard atomic mass
        convertMass(element) {
            var n = element.atomicNumber;
            var m = element.atomicMass;
            var exceptions = [
                57,
                58,
                59,
                60,
                62,
                63,
                64,
                65,
                66,
                67,
                68,
                69,
                70,
                71,
                90,
                91,
                92
            ];
            if (
                (n <= 83 && n !== 61 && n !== 43) ||
                exceptions.indexOf(n) > -1
            ) {
                m = m.slice(0, -3);
                return parseFloat(parseFloat(m).toFixed(3));
            } else {
                return m.toString();
            }
        }
    }
};
</script>

<style lang="scss" scoped>
.element {
    color: rgba(255, 255, 255, 0.55);
    width: 100%;
    height: 100%;
    max-width: 4.86vw;
    max-height: 4.86vw;
    overflow: hidden;
    text-align: center;
    padding: 0.2vw;
    transition: opacity 1s ease;
    .atomicnumber {
        text-align: left;
        color: rgba(255, 255, 255, 0.5);
        font-size: 0.65vw;
        span {
            float: right;
            color: rgba(255, 255, 255, 0);
            font-weight: 200;
        }
    }
    .name {
        font-size: 0.67vw;
        margin-top: -0.24vw;
        opacity: 0.9;
        font-weight: 200;
    }
    .symbol {
        font-weight: 600;
        font-size: 1.8vw;
        line-height: 2.5vw;
    }
    &:hover {
        color: rgba(255, 255, 255, 0.9);
    }
}
.preload {
    opacity: 0;
}
.l1 {
    transition-delay: 0ms;
}
.l2 {
    transition-delay: 100ms;
}
.l3 {
    transition-delay: 180ms;
}
.l4 {
    transition-delay: 260ms;
}
.l5 {
    transition-delay: 320ms;
}
.l6 {
    transition-delay: 380ms;
}
.l7 {
    transition-delay: 440ms;
}
.l8 {
    transition-delay: 500ms;
}
.l9 {
    transition-delay: 550ms;
}
.l10 {
    transition-delay: 600ms;
}
.l11 {
    transition-delay: 640ms;
}
.l12 {
    transition-delay: 670ms;
}
.l13 {
    transition-delay: 700ms; //
}
.alkali {
    background-color: rgba(95, 42, 53, 0.9);
    &:hover {
        background-color: rgba(100, 50, 60, 0.5);
    }
}
.alkaliEarth {
    background-color: rgba(95, 70, 55, 0.9);
    &:hover {
        background-color: rgba(93, 73, 61, 0.5);
    }
}
.transitionMetal {
    background-color: rgba(58, 70, 90, 0.9);
    &:hover {
        background-color: rgba(59, 73, 98, 0.5);
    }
}
.noble {
    background-color: rgba(87, 49, 126, 0.9);
    &:hover {
        background-color: rgba(96, 60, 130, 0.5);
    }
}
.halogen {
    background-color: rgba(77, 74, 150, 0.9);
    &:hover {
        background-color: rgba(102, 100, 161, 0.5);
    }
}
.nonMetal {
    background-color: rgba(52, 53, 109, 0.9);
    &:hover {
        background-color: rgba(46, 48, 108, 0.5);
    }
}
.metalloid {
    background-color: rgba(21, 84, 100, 0.9);
    &:hover {
        background-color: rgba(34, 74, 106, 0.5);
    }
}
.postTransition {
    background-color: rgba(28, 100, 73, 0.9);
    &:hover {
        background-color: rgba(34, 94, 79, 0.5);
    }
}
.lanthanoid {
    background-color: rgba(74, 57, 110, 0.9);
    &:hover {
        background-color: rgba(80, 67, 111, 0.5);
    }
}
.actinoid {
    background-color: rgba(64, 37, 80, 0.9);
    &:hover {
        background-color: rgba(62, 41, 73, 0.5);
    }
}
@media only screen and (max-width: 600px) {
    .element {
        width: 100%;
        height: 100%;
        box-sizing: border-box;
        text-align: center;
        padding: 0.4vw;
        transition: 0.2s;
        transition-timing-function: ease;
        .atomicnumber {
            text-align: left;
            font-size: 1.2vw;
            span {
                float: right;
            }
        }
        .name {
            font-size: 1.3vw;
            margin-top: 0;
            opacity: 0.9;
        }
        .symbol {
            font-weight: 600;
            font-size: 4vw;
            line-height: 4.5vw;
        }
    }
}
</style>
