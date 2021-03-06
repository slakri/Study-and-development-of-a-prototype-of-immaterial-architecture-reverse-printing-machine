## Interface

Another way to create different foam sculpture is to use microphone. During this project two possible ways were investigated, using which it should have been possible to create the already known foam fragments: curved and squared. It has been considered to upload a prototype version of interface that uses microphone to draw the squre-shaped foam fragments.

In order to achieve this goal, a **Minim** library was used, which is an audio library developed mainly for **Processing** developing. Its API makes integrating audio into the sketches as simple as possible, while still providing a lot of flexibility. More information about this library and its API can be found on http://code.compartmental.net/minim/.

Using Minim's API we want to create square-shaped foam fragments. For this purpose a special component of Minim's library was used: **FFT**, which can be included into a sketch using:
```java
import ddf.minim.*;
import ddf.minim.analysis.*;
```
This tool performs a fast Fourier transformation on audio data to generate a frequency spectrum. What allows us to make the square-shaped foam fragments out of it, is that FFT groups each individual frequence into an appropriate frequency band. Each band has its volume level. In such a way it is possible to adapt this tool to the purposes of this project. Having in general 64 frequency bands, we can create 64 different curve fragments during the simulation. What differs these fragments is the volume level, which corresponds to an appropriate number of degrees a step motor should move.

This prototype interface works as follows. On the left side of the screen there are three buttons. By clicking a **capture** button, the current FFT result in form of a frequency spectrum for both audio channels is drawn in form of the foam. This result is saved into appropriate arrays, which then will be sent via serial connection to the Arduino board, containing the rescaled information in degrees of the control points by clicking a button **send**.

If you can see, there is no Arduino source file attached. This is because a handling algorithm is just the same, described in the folder **squares**. If there are some questions regarding what methods were used to achive this result using Minim library, the Processing code is commented.

Experimental results were, however, not perfect because of the resolution. But it is directly connected with a fact, that usually a frequency spectrum looks in such a way that it has more or less recognizable information in its middle, whereas at low and high frequency bands there no recognizable peaks. Moreover within these 64 frequency bands, two neighbour bands usually do not differ drastically. All this leads to low recognizable results, because of the foam resolution. Trying to avoid this, some rescaling procedure could be done, but it will break the original FFT result.
