1. About:
===========

This project contains a small HTML project aimed to randomize the years mentioned in the "Back to the Future" trilogy (including years of alternate timelines) and display it all inside the movie's DeLorean console.

The application is HTML-based as the project would be displayed on an unknown platform.



2. Components:
===========

The project consists of a single HTML file - "randomizer.html".
The file contains several objects:

* 4 digits images (identified as "D1", "D2", "D3" and "D4")
* AM/PM indicator image, used to indicate "alternate" timeline (identified as "D5")
* File input to choose a text file with a years list (identified as "fileInput")
* "Hide buttons" input button
* Instructions DIV (identified as "instructions") on howto use the application (with a button that hide the DIV on click)


3. Flow:
===========

* We use the file input to choose the years list file - the downside of HTML client-side usage, is that we can't automatically load the years file (assuming it is ready when activated) due to security reasons. We must first load it via the file input, and only then we may continue.
* The "Hide buttons" simply hides the file input and itself (and if the instructions DIV wasn't hidden yet, it'll also hide it as well). When the "Hide buttons" is pressed, it means we've finished preparing the page, and we can display it to an audience.
* We start the randomization process by clicking any of the 4 digits (D1-D4). The click has 3 options:
  - If we're already in a randomization process, do nothing
  - If we've already loaded the file, randomize once more
  - If we haven't loaded the file yet, load it first, and then activate the randomization process
* Loading the file - we load the file using a FileReader object and the readAsText method on the input file. Since the FileReader as async, we continue on its onload event (fileReaderLoaded). The file is parsed to text array of lines (yearsArr)
* Randomization is done by randomizing an index from the yearsArr and displaying it (first 4 digits in 7-segment display of the year, suffix "A" if alternate). We also have an iteration counter, than runs 25times - we 400ms before calling the next iteration to let the audience enough time to the see the display. When the iterations are done, we remove the chosen index from yearsArr so it won't be selected again (we can re-run another 25 iterations by clicking again the digits)


4. Graphics:
===========

Aligning the graphics was the most challanging part.

The console image was taken from http://ashevillealetrail.com/asheville-craft-beer-event/bearwaters-brewings-back-to-the-future-countdown/#.VgmrOZeBL4s
 
and was changed to have the green year digits blank, and also set the PM led off.

Green 7-segment images were based on https://scott-inkscape.googlecode.com/hg/seven-segment/glow-green/ with slight colour changes to the off leds.

To mark that "alternate" is on, both AM and PM leds were on, so a picture copying the PM led to the AM spot was created.


