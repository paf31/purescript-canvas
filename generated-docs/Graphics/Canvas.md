## Module Graphics.Canvas

This module defines foreign types and functions for working with the 2D
Canvas API.

#### `CANVAS`

``` purescript
data CANVAS :: Effect
```

The `Canvas` effect denotes computations which read/write from/to the canvas.

#### `CanvasElement`

``` purescript
data CanvasElement :: Type
```

A canvas HTML element.

#### `Context2D`

``` purescript
data Context2D :: Type
```

A 2D graphics context.

#### `ImageData`

``` purescript
data ImageData :: Type
```

An image data object, used to store raster data outside the canvas.

#### `CanvasImageSource`

``` purescript
data CanvasImageSource :: Type
```

Opaque object for drawing elements and things to the canvas.

#### `Arc`

``` purescript
type Arc = { x :: Number, y :: Number, r :: Number, start :: Number, end :: Number }
```

A type representing an arc object:

- The center coordinates `x` and `y`,
- The radius `r`,
- The starting and ending angles, `start` and `end`.

#### `Composite`

``` purescript
data Composite
  = SourceOver
  | SourceIn
  | SourceOut
  | SourceAtop
  | DestinationOver
  | DestinationIn
  | DestinationOut
  | DestinationAtop
  | Lighter
  | Copy
  | Xor
  | Multiply
  | Screen
  | Overlay
  | Darken
  | Lighten
  | ColorDodge
  | ColorBurn
  | HardLight
  | SoftLight
  | Difference
  | Exclusion
  | Hue
  | Saturation
  | Color
  | Luminosity
```

Enumerates the different types of composite operations and blend modes.

##### Instances
``` purescript
Show Composite
```

#### `Dimensions`

``` purescript
type Dimensions = { width :: Number, height :: Number }
```

Canvas dimensions (width and height) in pixels.

#### `LineCap`

``` purescript
data LineCap
  = Round
  | Square
  | Butt
```

Enumerates the different types of line cap.

##### Instances
``` purescript
Eq LineCap
```

#### `LineJoin`

``` purescript
data LineJoin
  = BevelJoin
  | RoundJoin
  | MiterJoin
```

Enumerates the different types of line join

#### `Rectangle`

``` purescript
type Rectangle = { x :: Number, y :: Number, w :: Number, h :: Number }
```

A type representing a rectangle object:

- The top-left corner coordinates `x` and `y`,
- The width and height `w` and `h`.

#### `ScaleTransform`

``` purescript
type ScaleTransform = { scaleX :: Number, scaleY :: Number }
```

An object representing a scaling transform:

- The scale factors in the `x` and `y` directions, `scaleX` and `scaleY`.

#### `TextMetrics`

``` purescript
type TextMetrics = { width :: Number }
```

Text metrics:

- The text width in pixels.

#### `Transform`

``` purescript
type Transform = { m11 :: Number, m12 :: Number, m21 :: Number, m22 :: Number, m31 :: Number, m32 :: Number }
```

An object representing a general transformation as a homogeneous matrix.

#### `TranslateTransform`

``` purescript
type TranslateTransform = { translateX :: Number, translateY :: Number }
```

An object representing a translation:

- The translation amounts in the `x` and `y` directions, `translateX` and `translateY`.

#### `TextAlign`

``` purescript
data TextAlign
  = AlignLeft
  | AlignRight
  | AlignCenter
  | AlignStart
  | AlignEnd
```

Enumerates types of text alignment.

##### Instances
``` purescript
Show TextAlign
```

#### `CanvasPattern`

``` purescript
data CanvasPattern :: Type
```

Opaque object describing a pattern.

#### `PatternRepeat`

``` purescript
data PatternRepeat
  = Repeat
  | RepeatX
  | RepeatY
  | NoRepeat
```

Enumerates the different types of pattern repetitions.

##### Instances
``` purescript
Show PatternRepeat
```

#### `CanvasGradient`

``` purescript
data CanvasGradient :: Type
```

Opaque object describing a gradient.

#### `LinearGradient`

``` purescript
type LinearGradient = { x0 :: Number, y0 :: Number, x1 :: Number, y1 :: Number }
```

A type representing a linear gradient.
 -  Starting point coordinates: (`x0`, `y0`)
 -  Ending point coordinates: (`x1`, `y1`)

#### `RadialGradient`

``` purescript
type RadialGradient = { x0 :: Number, y0 :: Number, r0 :: Number, x1 :: Number, y1 :: Number, r1 :: Number }
```

A type representing a radial gradient.
 -  Starting circle center coordinates: (`x0`, `y0`)
 -  Starting circle radius: `r0`
 -  Ending circle center coordinates: (`x1`, `y1`)
 -  Ending circle radius: `r1`

#### `QuadraticCurve`

``` purescript
type QuadraticCurve = { cpx :: Number, cpy :: Number, x :: Number, y :: Number }
```

A type representing a quadratic Bézier curve.
 - Bézier control point: (`cpx`, `cpy`)
 - Ending point coordinates: (`x`, `y`)

#### `BezierCurve`

``` purescript
type BezierCurve = { cp1x :: Number, cp1y :: Number, cp2x :: Number, cp2y :: Number, x :: Number, y :: Number }
```

A type representing a cubic Bézier curve.
 - First Bézier control point: (`cp1x`, `cp1y`)
 - Second Bézier control point: (`cp2x`, `cp2y`)
 - Ending point: (`x`, `y`)

#### `getCanvasElementById`

``` purescript
getCanvasElementById :: forall eff. String -> Eff (canvas :: CANVAS | eff) (Maybe CanvasElement)
```

Get a canvas element by ID, or `Nothing` if the element does not exist.

#### `getContext2D`

``` purescript
getContext2D :: forall eff. CanvasElement -> Eff (canvas :: CANVAS | eff) Context2D
```

Get the 2D graphics context for a canvas element.

#### `getCanvasWidth`

``` purescript
getCanvasWidth :: forall eff. CanvasElement -> Eff (canvas :: CANVAS | eff) Number
```

Get the canvas width in pixels.

#### `setCanvasWidth`

``` purescript
setCanvasWidth :: forall eff. CanvasElement -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Set the canvas width in pixels.

#### `getCanvasHeight`

``` purescript
getCanvasHeight :: forall eff. CanvasElement -> Eff (canvas :: CANVAS | eff) Number
```

Get the canvas height in pixels.

#### `setCanvasHeight`

``` purescript
setCanvasHeight :: forall eff. CanvasElement -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Set the canvas height in pixels.

#### `getCanvasDimensions`

``` purescript
getCanvasDimensions :: forall eff. CanvasElement -> Eff (canvas :: CANVAS | eff) Dimensions
```

Get the canvas dimensions in pixels.

#### `setCanvasDimensions`

``` purescript
setCanvasDimensions :: forall eff. CanvasElement -> Dimensions -> Eff (canvas :: CANVAS | eff) Unit
```

Set the canvas dimensions in pixels.

#### `canvasToDataURL`

``` purescript
canvasToDataURL :: forall eff. CanvasElement -> Eff (canvas :: CANVAS | eff) String
```

Create a data URL for the current canvas contents

#### `setLineWidth`

``` purescript
setLineWidth :: forall eff. Context2D -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current line width.

#### `setFillStyle`

``` purescript
setFillStyle :: forall eff. Context2D -> String -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current fill style/color.

#### `setStrokeStyle`

``` purescript
setStrokeStyle :: forall eff. Context2D -> String -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current stroke style/color.

#### `setShadowBlur`

``` purescript
setShadowBlur :: forall eff. Context2D -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current shadow blur radius.

#### `setShadowOffsetX`

``` purescript
setShadowOffsetX :: forall eff. Context2D -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current shadow x-offset.

#### `setShadowOffsetY`

``` purescript
setShadowOffsetY :: forall eff. Context2D -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current shadow y-offset.

#### `setShadowColor`

``` purescript
setShadowColor :: forall eff. Context2D -> String -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current shadow color.

#### `setMiterLimit`

``` purescript
setMiterLimit :: forall eff. Context2D -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current miter limit.

#### `setLineCap`

``` purescript
setLineCap :: forall eff. Context2D -> LineCap -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current line cap type.

#### `setLineJoin`

``` purescript
setLineJoin :: forall eff. Context2D -> LineJoin -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current line join type.

#### `setGlobalCompositeOperation`

``` purescript
setGlobalCompositeOperation :: forall eff. Context2D -> Composite -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current composite operation.

#### `setGlobalAlpha`

``` purescript
setGlobalAlpha :: forall eff. Context2D -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current global alpha level.

#### `beginPath`

``` purescript
beginPath :: forall eff. Context2D -> Eff (canvas :: CANVAS | eff) Unit
```

Begin a path object.

#### `stroke`

``` purescript
stroke :: forall eff. Context2D -> Eff (canvas :: CANVAS | eff) Unit
```

Stroke the current object.

#### `fill`

``` purescript
fill :: forall eff. Context2D -> Eff (canvas :: CANVAS | eff) Unit
```

Fill the current object.

#### `clip`

``` purescript
clip :: forall eff. Context2D -> Eff (canvas :: CANVAS | eff) Unit
```

Clip to the current object.

#### `lineTo`

``` purescript
lineTo :: forall eff. Context2D -> Number -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Move the path to the specified coordinates, drawing a line segment.

#### `moveTo`

``` purescript
moveTo :: forall eff. Context2D -> Number -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Move the path to the specified coordinates, without drawing a line segment.

#### `closePath`

``` purescript
closePath :: forall eff. Context2D -> Eff (canvas :: CANVAS | eff) Unit
```

Close the current path.

#### `strokePath`

``` purescript
strokePath :: forall eff a. Context2D -> Eff (canvas :: CANVAS | eff) a -> Eff (canvas :: CANVAS | eff) a
```

A convenience function for drawing a stroked path.

For example:

```purescript
strokePath ctx $ do
  moveTo ctx 10.0 10.0
  lineTo ctx 20.0 20.0
  lineTo ctx 10.0 20.0
  closePath ctx
```

#### `fillPath`

``` purescript
fillPath :: forall eff a. Context2D -> Eff (canvas :: CANVAS | eff) a -> Eff (canvas :: CANVAS | eff) a
```

A convenience function for drawing a filled path.

For example:

```purescript
fillPath ctx $ do
  moveTo ctx 10.0 10.0
  lineTo ctx 20.0 20.0
  lineTo ctx 10.0 20.0
  closePath ctx
```

#### `arc`

``` purescript
arc :: forall eff. Context2D -> Arc -> Eff (canvas :: CANVAS | eff) Unit
```

Render an arc object.

#### `rect`

``` purescript
rect :: forall eff. Context2D -> Rectangle -> Eff (canvas :: CANVAS | eff) Unit
```

Render a rectangle.

#### `fillRect`

``` purescript
fillRect :: forall eff. Context2D -> Rectangle -> Eff (canvas :: CANVAS | eff) Unit
```

Fill a rectangle.

#### `strokeRect`

``` purescript
strokeRect :: forall eff. Context2D -> Rectangle -> Eff (canvas :: CANVAS | eff) Unit
```

Stroke a rectangle.

#### `clearRect`

``` purescript
clearRect :: forall eff. Context2D -> Rectangle -> Eff (canvas :: CANVAS | eff) Unit
```

Clear a rectangle.

#### `scale`

``` purescript
scale :: forall eff. Context2D -> ScaleTransform -> Eff (canvas :: CANVAS | eff) Unit
```

Apply a scaling transform.

#### `rotate`

``` purescript
rotate :: forall eff. Context2D -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Apply a rotation.

#### `translate`

``` purescript
translate :: forall eff. Context2D -> TranslateTransform -> Eff (canvas :: CANVAS | eff) Unit
```

Apply a translation

#### `transform`

``` purescript
transform :: forall eff. Context2D -> Transform -> Eff (canvas :: CANVAS | eff) Unit
```

Apply a general transformation to the current transformation matrix

#### `setTransform`

``` purescript
setTransform :: forall eff. Context2D -> Transform -> Eff (canvas :: CANVAS | eff) Unit
```

Set the transformation matrix

#### `textAlign`

``` purescript
textAlign :: forall eff. Context2D -> Eff (canvas :: CANVAS | eff) TextAlign
```

Get the current text alignment.

#### `setTextAlign`

``` purescript
setTextAlign :: forall eff. Context2D -> TextAlign -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current text alignment.

#### `font`

``` purescript
font :: forall eff. Context2D -> Eff (canvas :: CANVAS | eff) String
```

Get the current font.

#### `setFont`

``` purescript
setFont :: forall eff. Context2D -> String -> Eff (canvas :: CANVAS | eff) Unit
```

Set the current font.

#### `fillText`

``` purescript
fillText :: forall eff. Context2D -> String -> Number -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Fill some text.

#### `strokeText`

``` purescript
strokeText :: forall eff. Context2D -> String -> Number -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Stroke some text.

#### `measureText`

``` purescript
measureText :: forall eff. Context2D -> String -> Eff (canvas :: CANVAS | eff) TextMetrics
```

Measure some text.

#### `save`

``` purescript
save :: forall eff. Context2D -> Eff (canvas :: CANVAS | eff) Unit
```

Save the current context.

#### `restore`

``` purescript
restore :: forall eff. Context2D -> Eff (canvas :: CANVAS | eff) Unit
```

Restore the previous context.

#### `withContext`

``` purescript
withContext :: forall eff a. Context2D -> Eff (canvas :: CANVAS | eff) a -> Eff (canvas :: CANVAS | eff) a
```

A convenience function: run the action, preserving the existing context.

For example, outside this block, the fill style is preseved:

```purescript
withContext ctx $ do
  setFillStyle "red" ctx
  ...
```

#### `tryLoadImage`

``` purescript
tryLoadImage :: forall eff. String -> (Maybe CanvasImageSource -> Eff (canvas :: CANVAS | eff) Unit) -> Eff (canvas :: CANVAS | eff) Unit
```

Asynchronously load an image file by specifying its path.

#### `getImageData`

``` purescript
getImageData :: forall eff. Context2D -> Number -> Number -> Number -> Number -> Eff (canvas :: CANVAS | eff) ImageData
```

Get image data for a portion of the canvas.

#### `putImageData`

``` purescript
putImageData :: forall eff. Context2D -> ImageData -> Number -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Set image data for a portion of the canvas.

#### `putImageDataFull`

``` purescript
putImageDataFull :: forall eff. Context2D -> ImageData -> Number -> Number -> Number -> Number -> Number -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

Set image data for a portion of the canvas.

#### `createImageData`

``` purescript
createImageData :: forall eff. Context2D -> Number -> Number -> Eff (canvas :: CANVAS | eff) ImageData
```

Create an image data object.

#### `createImageDataCopy`

``` purescript
createImageDataCopy :: forall eff. Context2D -> ImageData -> Eff (canvas :: CANVAS | eff) ImageData
```

Create a copy of an image data object.

#### `imageDataWidth`

``` purescript
imageDataWidth :: ImageData -> Int
```

Get the width of an `ImageData` object.

#### `imageDataHeight`

``` purescript
imageDataHeight :: ImageData -> Int
```

Get the height of an `ImageData` object.

#### `imageDataBuffer`

``` purescript
imageDataBuffer :: ImageData -> Uint8ClampedArray
```

Get the underlying buffer from an `ImageData` object.

#### `canvasElementToImageSource`

``` purescript
canvasElementToImageSource :: CanvasElement -> CanvasImageSource
```

#### `drawImage`

``` purescript
drawImage :: forall eff. Context2D -> CanvasImageSource -> Number -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

#### `drawImageScale`

``` purescript
drawImageScale :: forall eff. Context2D -> CanvasImageSource -> Number -> Number -> Number -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

#### `drawImageFull`

``` purescript
drawImageFull :: forall eff. Context2D -> CanvasImageSource -> Number -> Number -> Number -> Number -> Number -> Number -> Number -> Number -> Eff (canvas :: CANVAS | eff) Unit
```

#### `createPattern`

``` purescript
createPattern :: forall eff. Context2D -> CanvasImageSource -> PatternRepeat -> Eff (canvas :: CANVAS | eff) CanvasPattern
```

Create a new canvas pattern (repeatable image).

#### `setPatternFillStyle`

``` purescript
setPatternFillStyle :: forall eff. Context2D -> CanvasPattern -> Eff (canvas :: CANVAS | eff) Unit
```

Set the Context2D fillstyle to the CanvasPattern.

#### `createLinearGradient`

``` purescript
createLinearGradient :: forall eff. Context2D -> LinearGradient -> Eff (canvas :: CANVAS | eff) CanvasGradient
```

Create a linear CanvasGradient.

#### `createRadialGradient`

``` purescript
createRadialGradient :: forall eff. Context2D -> RadialGradient -> Eff (canvas :: CANVAS | eff) CanvasGradient
```

Create a radial CanvasGradient.

#### `addColorStop`

``` purescript
addColorStop :: forall eff. CanvasGradient -> Number -> String -> Eff (canvas :: CANVAS | eff) Unit
```

Add a single color stop to a CanvasGradient.

#### `setGradientFillStyle`

``` purescript
setGradientFillStyle :: forall eff. Context2D -> CanvasGradient -> Eff (canvas :: CANVAS | eff) Unit
```

Set the Context2D fillstyle to the CanvasGradient.

#### `quadraticCurveTo`

``` purescript
quadraticCurveTo :: forall eff. Context2D -> QuadraticCurve -> Eff (canvas :: CANVAS | eff) Unit
```

Draw a quadratic Bézier curve.

#### `bezierCurveTo`

``` purescript
bezierCurveTo :: forall eff. Context2D -> BezierCurve -> Eff (canvas :: CANVAS | eff) Unit
```

Draw a cubic Bézier curve.


