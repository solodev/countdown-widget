# countdown-widget

Countdown widgets have many uses on the web, the most common of which you will find on websites with products or services that haven't "launched" yet with a countdown widget displaying the time until their product and/or service launches. Alternate common coundown widget uses are upcoming holidays, events, conferences, etc. A countdown widget has several use cases yet it provides a sense of urgency to your call to action as it is now time sensitive. In this article, [Solodev](https://www.solodev.com/blog/) will teach you how to add a countdown widget to your website using HTML, CSS, and JavaScript. 

## Tutorial

For detailed instructions, vew Solodev's [Creating a Countdown Widget for your Website](https://www.solodev.com/blog/web-design/creating-a-countdown-widget-for-your-website.stml) article.

## Demo

Try out a working example on [JSFiddle](https://jsfiddle.net/solodev/hzshto8r/).

## HTML

The countdown widget contains the following basic HTML markup.

```
<div class="container">
<div class="well">
<div class="counter" id="clockdiv">
   <span class="title">Next Showing</span>
   <div class="sq">
      <span class="days bord">1</span> <span class="smalltext">Days</span>
   </div>
   <div class="sq">
      <span class="hours bord">22</span> <span class="smalltext">Hours</span>
   </div>
   <div class="sq">
      <span class="minutes bord">40</span> <span class="smalltext">Mins</span>
   </div>
   <div class="sq">
      <span class="seconds bord">45</span> <span class="smalltext">Secs</span>
   </div>
</div>
</div>
```

## CSS

All required CSS is in countdown-widget.css

## JavaScript

The following JavaScript powers the countdown widget.
```
$( document ).ready(function() {
function getTimeRemaining(endtime) {
  var t = Date.parse(endtime) - Date.parse(new Date());
  if (t<0) { return false; }
  var seconds = Math.floor((t / 1000) % 60);
  var minutes = Math.floor((t / 1000 / 60) % 60);
  var hours = Math.floor((t / (1000 * 60 * 60)) % 24);
  var days = Math.floor(t / (1000 * 60 * 60 * 24));
  return {
    'total': t,
    'days': days,
    'hours': hours,
    'minutes': minutes,
    'seconds': seconds
  };
}
function initializeClock(id, endtime) {
  var clock = document.getElementById(id);
  var daysSpan = clock.querySelector('.days');
  var hoursSpan = clock.querySelector('.hours');
  var minutesSpan = clock.querySelector('.minutes');
  var secondsSpan = clock.querySelector('.seconds');
  function updateClock() {
    var t = getTimeRemaining(endtime);
    if (t) {
      daysSpan.innerHTML = t.days;
      hoursSpan.innerHTML = ('0' + t.hours).slice(-2);
      minutesSpan.innerHTML = ('0' + t.minutes).slice(-2);
      secondsSpan.innerHTML = ('0' + t.seconds).slice(-2);
    } else {
      clearInterval(timeinterval);
      $('.broadcast .sq').hide();
      $('.broadcast .title').html('<a href="http://unite.bcctv.org/" class="button" style="padding:10px; height:60px; top:20px;">Watch Service Now!</a>');
    }
  }
 
  updateClock();
  var timeinterval = setInterval(updateClock, 1000);
}
var deadline = new Date(); //today
deadline.setDate(deadline.getDate() + 7);
initializeClock('clockdiv', deadline);
});

```
## External Includes

This tutorial includes the following third party resources.
```
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
<link rel="stylesheet" href="countdown-widget.css">
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
<script src="countdown-widget.js"></script>
```
