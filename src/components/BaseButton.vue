<template>
  <component
    :is="tag"
    :href="href"
    :target="target"
    :type="computedType"
    class="button"
    :class="buttonClasses"
  >
    <i v-if="iconClasses" :class="iconClasses" />
    <span v-if="$slots.default" :class="textClasses">
      <slot />
    </span>
  </component>
</template>

<script setup>
const props = defineProps({
  href: {
    type: String,
    required: false,
    default: null,
  },
  target: {
    type: String,
    required: false,
    default: null,
  },
  type: {
    type: String,
    required: false,
    default: null,
  },
  variation: {
    type: String,
    required: false,
    default: 'outline-main',
  },
  size: {
    type: String,
    required: false,
    default: null,
  },
  iconClasses: {
    type: String,
    required: false,
    default: null,
  },
  textClasses: {
    type: String,
    required: false,
    default: null,
  },
})

const tag = props.href ? 'a' : 'button'

const computedType = !props.type && !props.href ? 'button' : null

const buttonClasses = {
  'button--fill-main': props.variation === 'fill-main',
  'button--fill-neutral': props.variation === 'fill-neutral',
  'button--outline-main': props.variation === 'outline-main',
  'button--outline-neutral': props.variation === 'outline-neutral',
  'button--text-main': props.variation === 'text-main',
  'button--text-neutral': props.variation === 'text-neutral',
  'button--small': props.size === 'small',
  'button--medium': props.size === 'medium',
  'button--large': props.size === 'large',
}
</script>

<style scoped>
.button {
  font-family: var(--font-main);
  font-weight: 600;
  text-transform: uppercase;
  cursor: pointer;
  border-radius: 0.5rem;
  padding: 0.5rem 1rem;
  transition:
    color 0.32s ease,
    background-color 0.32s ease,
    border 0.32s ease;
  outline: none;
}

.button i + span {
  margin-left: 0.5rem;
}

.button--fill-main {
  color: white;
  background-color: var(--color-main);
  border: 2px solid var(--color-main);
}

.button--fill-main:focus,
.button--fill-main:hover {
  background-color: var(--color-main--light);
  border-color: var(--color-main--light);
}

.button--fill-main:active {
  background-color: var(--color-main--dark);
  border-color: var(--color-main--dark);
}

.button--fill-neutral {
  color: white;
  background-color: var(--gray-400);
  border: 2px solid var(--gray-400);
}

.button--fill-neutral:focus,
.button--fill-neutral:hover {
  background-color: var(--gray-200);
  border-color: var(--gray-200);
}

.button--fill-neutral:active {
  background-color: var(--gray-600);
  border-color: var(--gray-600);
}

.button--outline-main {
  color: var(--color-main);
  background-color: transparent;
  border: 2px solid var(--color-main);
}

.button--outline-main:focus,
.button--outline-main:hover {
  color: white;
  background-color: var(--color-main);
}

.button--outline-main:active {
  background-color: var(--color-main--dark);
}

.button--outline-neutral {
  color: var(--gray-400);
  background-color: transparent;
  border: 2px solid var(--gray-400);
}

.button--outline-neutral:focus,
.button--outline-neutral:hover {
  color: white;
  background-color: var(--gray-400);
}

.button--outline-neutral:active {
  background-color: var(--gray-600);
}

.button--text-main {
  color: var(--color-main);
  background-color: transparent;
  border: 2px solid transparent;
}

.button--text-main:focus,
.button--text-main:hover {
  color: var(--color-main--light);
}

.button--text-main:focus {
  border: 2px solid var(--color-main--light);
}

.button--text-neutral {
  color: var(--gray-400);
  background-color: transparent;
  border: 2px solid transparent;
}

.button--text-neutral:focus,
.button--text-neutral:hover {
  color: var(--color-main);
}

.button--text-neutral:focus {
  border: 2px solid var(--color-main);
}

.button--small {
  font-size: 0.75rem;
}

.button--medium {
  font-size: 1.5rem;
}

.button--large {
  font-size: 2.5rem;
}
</style>
