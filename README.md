
# Submission After First Review
- Added length in getting length from getElementsByClassName, so pizza can resize.

# Submission Before Review

## RUNNING

### How to run and check the frontend-nanodegree-mobile-portfolio/index.html and pizza.html
- In your command window, type 'python -m SimpleHTTPServer' from same folder where index.html file is.
- then type '127.0.0.1.8000' on your Google Chrome Canary browser to see the portfolio
- To access the local server remotely on Google Pagespeed, open another command window and type '(the folder where ngrok is)/ngrok 8000' and then copy and paste the https://.. address to Google Pagespped page.

### Can see the website at http://sdiwana.github.io/frontend-nanodegree-mobile-portfolio/


### How to run and view 60 FPS Check:
- Click Pizza link on your local host (127.0.0.1.8000) after following the first two steps above.
- Start Google DevTool, click start button (left most round button) on Timeline tab, and scroll up and down with mouse on pizza page for about 6-8 times.
- Click on same left most round button to stop recording timeline, and check the timeline graph.
- Now check Console tab to get the 10 frames rate.

### How to rrun and view Pizza Sizing Check:
- Start Google DevTool and resize pizza on the pizza sizing bar couple of times.
- Check Console tab on DevTool to see the pizza resizing time.

## CHANGES TO CODE

### Changes to index.html for Google PageSpeed of greater than 90
- Optimized images though Google Pagespeed suggestion link
- Moved, minifiedå, and inlined style.css to bottom.  Used http://cssminifier.com/ to minify
- Inlined google font - see @fontface in the style.
- Added media type to print.css
- Moved all scripts to bottom
- Added async to analytics.js

### Changes to views/main.js and views/css/style.css to improve Frame Per Second
- Changed all QuerySelectorAll and QuerySelector calls to getElementbyClassName and Id.
- Removed pizza image loading from for loops to load it only once
- Moving pizzasDiv assignment out of for loop from pizza appending function at load time
- Changes to updatePositions() function
- Moved items assignment out of for loop
- Moved top calculation out of for loop
- Calculated and assigned 5 phases to an phaseArray
- Calculated and assigned 8 left values to leftArray
- Calculated left first with phaseArray and leftArray
- Used transform and translate3d and translateZ, so hardware acceleration is used, and elements are forced into their own composite layers.  Also, eliminated changing the DOM left.
- Added requestAnimationFrame to call update position to run updatePositions on scroll
- Decreased 200 down to an arbitrary number of 24, in addEventListener for DOMContentLoaded
- Added backface-visibility: hidden to views/css/style.js to reduce paint time

### Changes to views/main.js, changePizzaSizes() function, to reduce pizza resizing time
- Moved the dx and newwidth calculation out of for loop.
- Moved length calculation out of for loop

### Added Optimized folder of Views folder, and used optimized images

## Resources
- Made use of suggestions on Google Pagespeed
- Used minify resources, https://developers.google.com/speed/docs/insights/MinifyResources
- Saw office hours - https://plus.google.com/events/c8eah6f0d0t9eretebpm7dqi0ok?authkey=CKaNhtb0quvqKA
- fend office hours - https://github.com/udacity/fend-office-hours/tree/master/Web%20Optimization/Effective%20Optimizations%20for%2060%20FPS
- Read http://www.phpied.com/rendering-repaint-reflowrelayout-restyle/
- Read https://github.com/mikejoyceio/website-optimization
- Many other google search on css optimizations


## Problems
- Tried installing GULP and ran out of memory, did not try Crunch after that!
- Thought of base64, but read it increases the image and html size, need to do more research,
http://stackoverflow.com/questions/5258057/should-i-embed-images-as-data-base64-in-css-or-html, and checkout out the: http://www.base64-image.de/step-2.php
- Didn't quite understand how to convert google font to base64 Optimal, since I am not uploading the font.  Instead, inlined the 'cyrillic-ext' of
http://fonts.googleapis.com/css?family=Open+Sans:400,700 link. Looked at http://www.fontsquirrel.com/tools/webfont-generator



## Website Performance Optimization portfolio project

Your challenge, if you wish to accept it (and we sure hope you will), is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques you've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

To get started, check out the repository, inspect the code,

### Getting started

####Part 1: Optimize PageSpeed Insights score for index.html

Some useful tips to help you get started:

1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

Profile, optimize, measure... and then lather, rinse, and repeat. Good luck!

####Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher. You will find instructive comments in main.js.

You might find the FPS Counter/HUD Display useful in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).

### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>

### Sample Portfolios

Feeling uninspired by the portfolio? Here's a list of cool portfolios I found after a few minutes of Googling.

* <a href="http://www.reddit.com/r/webdev/comments/280qkr/would_anybody_like_to_post_their_portfolio_site/">A great discussion about portfolios on reddit</a>
* <a href="http://ianlunn.co.uk/">http://ianlunn.co.uk/</a>
* <a href="http://www.adhamdannaway.com/portfolio">http://www.adhamdannaway.com/portfolio</a>
* <a href="http://www.timboelaars.nl/">http://www.timboelaars.nl/</a>
* <a href="http://futoryan.prosite.com/">http://futoryan.prosite.com/</a>
* <a href="http://playonpixels.prosite.com/21591/projects">http://playonpixels.prosite.com/21591/projects</a>
* <a href="http://colintrenter.prosite.com/">http://colintrenter.prosite.com/</a>
* <a href="http://calebmorris.prosite.com/">http://calebmorris.prosite.com/</a>
* <a href="http://www.cullywright.com/">http://www.cullywright.com/</a>
* <a href="http://yourjustlucky.com/">http://yourjustlucky.com/</a>
* <a href="http://nicoledominguez.com/portfolio/">http://nicoledominguez.com/portfolio/</a>
* <a href="http://www.roxannecook.com/">http://www.roxannecook.com/</a>
* <a href="http://www.84colors.com/portfolio.html">http://www.84colors.com/portfolio.html</a>
