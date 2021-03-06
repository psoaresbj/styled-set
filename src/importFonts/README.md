# importFonts

> Import font files from theme fonts variables config array

## Usage

- Set your font config array and formats (not required)

```jsx
import React from 'react'
import { ThemeProvider } from 'styled-components'
import colors from 'colors'

const weights = { light: 300, regular: 400, bold: 600 }

const theme = {
  colors,
  weights,
  fonts: {
    families: { sans: 'IBM Plex Sans' },
    sizes: { sm: 14, base: 16, lg: 18 },
    // formats are optional
    // the function will use
    // the defaults Woff and Woff2
    formats: ['woff2', 'ttf'],
    config: [
      // be sure you add the
      // right path and prefix
      // and if you want your
      // app try to get fonts
      // locally, just add
      // localLoading opt
      //
      // with this example we
      // are importing:
      //  IBM Plex Sans Light from `fonts/IBMPlexSans/IBMPlexSans-light.woff`
      //  IBM Plex Sans Regular from `fonts/IBMPlexSans/IBMPlexSans-regular.woff`
      //  IBM Plex Sans Bold from `fonts/IBMPlexSans/IBMPlexSans-bold.woff`
      { family: 'IBM Plex Sans', path: 'fonts/IBMPlexSans', prefix: 'IBMPlexSans-', weights, localLoading: true }
    ]
  }
}

const App = () => (
  <ThemeProvider theme={theme}>
    <div>
      {/* app content */}
    </div>
  </ThemeProvider>
)
```

- Use it in your global style component (you should have one)

```jsx
// GlobalStyle.js
import React from 'react'
import { createGlobalStyle } from 'styled-components'
import { importFonts } from 'styled-gen'

const GlobalStyle = createGlobalStyle`
  ${importFonts};

  body {
    font-family: ${({theme}) => theme.fonts.families.sans};
  }
`

export default GlobalStyle
```

```jsx
// Your base component
// child of ThemeProvider

//...
import GlobalStyle from './GlobalStyle'
//...

//...
render() {
  return (
    <GlobalStyle />
    {/* ... */}
  )
}
//...
```

## License

MIT © [psoaresbj](https://github.com/psoaresbj)