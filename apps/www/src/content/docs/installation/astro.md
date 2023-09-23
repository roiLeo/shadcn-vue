---
title: Astro
description: Install and configure Astro.
---

<Steps>

### Create project

Start by creating a new Astro project:

```bash
npm create astro@latest
```

### Configure your Astro project

You will be asked a few questions to configure your project:

```txt showLineNumbers
- Where should we create your new project?
./your-app-name
- How would you like to start your new project?
Choose a starter template (or Empty)
- Install dependencies?
Yes
- Do you plan to write TypeScript?
Yes
- How strict should TypeScript be?
Strict
- Initialize a new git repository? (optional)
Yes/No
```

### Add React to your project

Install React using the Astro CLI:

```bash
npx astro add react
```

<Callout class="mt-4">

Answer `Yes` to all the question prompted by the CLI when installing React.

</Callout>

### Add Tailwind CSS to your project

Install Tailwind CSS using the Astro CLI:

```bash
npx astro add tailwind
```

<Callout class="mt-4">

Answer `Yes` to all the question prompted by the CLI when installing Tailwind CSS.

</Callout>

### Edit tsconfig.json file

Add the code below to the tsconfig.json file to resolve paths:

```json {2-7} showLineNumbers
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    }
  }
}
```

### Run the CLI

Run the `shadcn-ui` init command to setup your project:

```bash
npx shadcn-ui@latest init
```

### Configure components.json

You will be asked a few questions to configure `components.json`:

```txt showLineNumbers
Would you like to use TypeScript (recommended)? no / yes
Which style would you like to use? › Default
Which color would you like to use as base color? › Slate
Where is your global CSS file? › › ./src/styles/globals.css
Do you want to use CSS variables for colors? › no / yes
Where is your tailwind.config.js located? › tailwind.config.cjs
Configure the import alias for components: › @/components
Configure the import alias for utils: › @/lib/utils
Are you using React Server Components? › no
```

### Import the globals.css file

Import the `globals.css` file in the `src/index.astro` file:

```ts {2} showLineNumbers
import '@/styles/globals.css'
```

### Update astro tailwind config

To prevent serving the Tailwind base styles twice, we need to tell Astro not to apply the base styles, since we already include them in our own `globals.css` file. To do this, set the `applyBaseStyles` config option for the tailwind plugin in `astro.config.mjs` to `false`.

```ts {3-5} showLineNumbers
export default defineConfig({
  integrations: [
    tailwind({
      applyBaseStyles: false,
    }),
  ],
})
```

### That's it

You can now start adding components to your project.

```bash
npx shadcn-ui@latest add button
```

The command above will add the `Button` component to your project. You can then import it like this:

```astro {2,10} showLineNumbers
---
import { Button } from "@/components/ui/button"
---

<html lang="en">
	<head>
		<title>Astro</title>
	</head>
	<body>
		<Button>Hello World</Button>
	</body>
</html>
```

</Steps>