<template>
  <q-btn v-bind="$props" :class="classes"/>
</template>
<script>
import { QBtn } from 'quasar'
export default {
  mixins: [ QBtn ],
  computed: {
    classes () {
      let colors

      if (this.color) {
        if (this.flat || this.outline) {
          colors = `text-theme2-${this.textColor || this.color}`
        } else {
          colors = `bg-theme2-${this.color} text-theme2-${this.textColor || 'white'}`
        }
      } else if (this.textColor) {
        colors = `text-theme2-${this.textColor}`
      }

      return `q-btn--${this.isRound ? 'round' : 'rectangle'}` +
        (colors !== void 0 ? ' ' + colors : '') +
        (this.isDisabled === true ? ' disabled' : ' q-focusable q-hoverable') +
        (this.fab === true ? ' q-btn--fab' : (this.fabMini === true ? ' q-btn--fab-mini' : '')) +
        (
          this.flat === true ? ' q-btn--flat' : (
            this.outline === true ? ' q-btn--outline' : (
              this.push === true ? ' q-btn--push' : (
                this.unelevated === true ? ' q-btn--unelevated' : ''
              )
            )
          )
        ) +
        (this.noCaps === true ? ' q-btn--no-uppercase' : '') +
        (this.rounded === true ? ' q-btn--rounded' : '') +
        (this.dense === true ? ' q-btn--dense' : '') +
        (this.stretch === true ? ' no-border-radius self-stretch' : '') +
        (this.glossy === true ? ' glossy' : '')
    }
  }
}
</script>
