---
title: "Determining Client Screen width for use in PHP"
date: 2008-06-11
forum: Programming Talk
---

### Post by brennydoogles on 2008-06-11
Hello, I am trying to figure out how to determine a User's screen width in Javascript, and have it available in PHP as a variable. I have done a bit of research, and I think that for my purposes this could be best accomplished by setting a cookie, but I have almost no knowledge of Javascript, and my PHP is weak. To make things slightly more complicated, I plan on putting this code in my head.php file, which is included in all of the pages on my site, so if setting a cookie requires that the page be refreshed, we will need to figure out how to do that to the correct page. Any help would be greatly appreciated!

---

### Post by LaRoza on 2008-06-11
> **brennydoogles said:**
> Hello, I am trying to figure out how to determine a User's screen width in Javascript, and have it available in PHP as a variable. I have done a bit of research, and I think that for my purposes this could be best accomplished by setting a cookie, but I have almost no knowledge of Javascript, and my PHP is weak. To make things slightly more complicated, I plan on putting this code in my head.php file, which is included in all of the pages on my site, so if setting a cookie requires that the page be refreshed, we will need to figure out how to do that to the correct page. Any help would be greatly appreciated!

Such calculations should be done on the client, not server. 

[php]
screen.height;
screen.width;
[/php]
Would be the ECMAScript for it, and you could send this in a form, or use it with Ajax.

---

### Post by brennydoogles on 2008-06-11
> **LaRoza said:**
> Such calculations should be done on the client, not server. 

[php]
screen.height;
screen.width;
[/php]
Would be the ECMAScript for it, and you could send this in a form, or use it with Ajax.

I understand that I would need to do this with Javascript, but my problem is that I don't know enough Javascript to make it work correctly. I was hoping to set the values as a cookie so that they may be easily accessed by PHP, but if there is a way to do this easily without relying on cookies I would be more than open to it. Any help would be awesome!

---

### Post by LaRoza on 2008-06-11
> **brennydoogles said:**
> I understand that I would need to do this with Javascript, but my problem is that I don't know enough Javascript to make it work correctly. I was hoping to set the values as a cookie so that they may be easily accessed by PHP, but if there is a way to do this easily without relying on cookies I would be more than open to it. Any help would be awesome!

Use Ajax, or use the ECMAScript to set it in a form to submit.

---

### Post by brennydoogles on 2008-06-12
> **LaRoza said:**
> Use Ajax, or use the ECMAScript to set it in a form to submit.

I guess the real question I'm getting at is... How would I do that? I don't think a form is a good option for me, since I will be using this to make determinations about layout based upon the users screen width. As for the AJAX, I only have the most vague clue on how it actually works, so writing the code is far beyond my grasp. I am more than willing to learn, but I also would like to be able to get started on my project ASAP. Thanks!

---

### Post by Pawka on 2008-06-12
The most stimple way would be read screen size with JavaScript and redirect page with parameters.

[html]
<script type="text/javascript">
window.onload  = function() {
        alert(screen.height);
        window.location = "http://www.somepage.com/index.php?h=" + screen.height + "&" + screen.width;
}
</script>
[/html]

But this way is not very cute. I don't like parameters in URLs :-) Also GET method should be used only to get data or format query, not to sending data. You can use AJAX. For AJAX you can try [script.aculo.us](http://script.aculo.us/) or [jQuery](http://www.jquery.com/) JavaScript libraries. There you'll find simple AJAX tutorials.

If you want use cookies, look at this page: [http://www.quirksmode.org/js/cookies.html](http://www.quirksmode.org/js/cookies.html)

Be careful and escape your input data :-)

---

### Post by MacAnthony on 2008-06-12
jQuery, as Pawka mentioned, would also work great to make layout changes on the fly too without having to go between the client and server and rerender the pages.

Here is the delemna you will have. You will have to load a page that will return that info (even if you store it in a cookie) so that you know how to render the page. In which case, having a form do this isn't a bad option. You need to have that initial page anyway, does it matter if it's a form?

---

### Post by brennydoogles on 2008-06-12
> **MacAnthony said:**
> jQuery, as Pawka mentioned, would also work great to make layout changes on the fly too without having to go between the client and server and rerender the pages.

Here is the delemna you will have. You will have to load a page that will return that info (even if you store it in a cookie) so that you know how to render the page. In which case, having a form do this isn't a bad option. You need to have that initial page anyway, does it matter if it's a form?

Well, I would think that a form would require the user to do something in order to submit the values, meaning inconvenience to the visitors. Am I wrong about this? It seems easier to have the site set a cookie once, and then redirect immediately and not have to do it again unless the cache gets cleared or the cookie expires.

---

### Post by MacAnthony on 2008-06-12
You could automatically submit a form just as easily as you could set a cookie and redirect the page via javascript. All personal preference on how to handle it.

---

### Post by brennydoogles on 2008-06-12
> **MacAnthony said:**
> You could automatically submit a form just as easily as you could set a cookie and redirect the page via javascript. All personal preference on how to handle it.

Interesting. I'm not sure how to do that (if you couldn't tell by the fact I didn't know it was possible), but that sounds like a good option. How would I go about doing it?

---

### Post by Pawka on 2008-06-13
You can autosubmit form when page is loaded by this way:

[HTML]
<script type="text/javascript">
        window.onload  = function() {
                var form = document.getElementById('form1');
                form.submit();
        }
</script>


<form id="form1" action="http://www.somepage.com/" method="POST">
        <input type="text" name="name" />
        <input type="submit" />
</form>
[/HTML]

You even don't need show input elements by setting type as "hidden". When you get screen size in php script, simply set values to seesion for later use. If you thinking about scripting with JavaScript, I strongly suggest try jQuery or script.aculo.us as I mention before. Scripting would be much easier.

---

### Post by Verminox on 2008-06-13
You must realise though that even if you send the width details to PHP, the next page that loads will be optimized for that screen width, but the user may simple resize the window or change the resolution and your objective might fail. Just keep this in mind when designing the application. Maybe you need to go back and rethink the design goals. Maybe you might find clearner solutions to optimizing the page for different screens, such as **CSS**.

---

### Post by brennydoogles on 2008-06-13
> **Verminox said:**
> You must realise though that even if you send the width details to PHP, the next page that loads will be optimized for that screen width, but the user may simple resize the window or change the resolution and your objective might fail. Just keep this in mind when designing the application. Maybe you need to go back and rethink the design goals. Maybe you might find clearner solutions to optimizing the page for different screens, such as **CSS**.

CSS is part of the solution. I have developed several stylesheets that are optimized for different screen widths, but I would also like to write a fumction that will add in line breaks every so often for smaller screens (mainly for use when I have multiple images that would be wider side-to-side than their parent element on narrow screens)does that make sense?

---

### Post by MacAnthony on 2008-06-13
> **Verminox said:**
> You must realise though that even if you send the width details to PHP, the next page that loads will be optimized for that screen width, but the user may simple resize the window or change the resolution and your objective might fail. Just keep this in mind when designing the application. Maybe you need to go back and rethink the design goals. Maybe you might find clearner solutions to optimizing the page for different screens, such as **CSS**.

Which is why I first recommended doing it client side with something like jquery. Not sure the types of modifications you would be making, but they might be just as easy/easier to do client side.

---

### Post by MacAnthony on 2008-06-13
> **brennydoogles said:**
> ...but I would also like to write a fumction that will add in line breaks every so often for smaller screens (mainly for use when I have multiple images that would be wider side-to-side than their parent element on narrow screens)does that make sense?

Line breaks are a poor solution for adjusting space as different operating systems will use different fonts having different metrics and different browsers will render them differently anyway.

I would just make a blank div with css and change it's height/width to the dimensions you want. It would be way more accurate.

---

### Post by brennydoogles on 2008-06-13
> **MacAnthony said:**
> Line breaks are a poor solution for adjusting space as different operating systems will use different fonts having different metrics and different browsers will render them differently anyway.

I would just make a blank div with css and change it's height/width to the dimensions you want. It would be way more accurate.

I have the images in question inside a div right now, but on smaller resolutions they are actually floating outside of the div. What I would like to do is have the br tag in one place on larger resolutions, and in another on the smaller resolutions (since I have the images arranged in a grid-esque format right now). Does that make more sense?


--Edit--

The moving br tags are temporary; I mean to eventually replace the entire thing with a good looking image gallery, but until I roll that out I want it to not look like crap on smaller monitors. I hope to replace the whole thing within a month, but it is a good learning experience until I can.

---

### Post by Verminox on 2008-06-14
> **brennydoogles said:**
> CSS is part of the solution. I have developed several stylesheets that are optimized for different screen widths, but I would also like to write a fumction that will add in line breaks every so often for smaller screens (mainly for use when I have multiple images that would be wider side-to-side than their parent element on narrow screens)does that make sense?

By using CSS you should be able to optimize your divs for all **screen** resolutions (PC, Mac) which would resize/overflow/float in such a way that the images appear wider horizontally on big resolutions and if the resolution is small or the window is resized then they would appear one below the other or whatever.

If you want to optimize for PDAs, Cell Phones, etc. you can just use the **handheld** media type to add a whole different stylesheet to the elements that you wanna change to optimize for narrow screens.

Client side code to manipulate visual display while workable is messy, often buggy and not well supported (especially on handhelds), not guarenteed to work always, and too much reliance on the script could mean that a non-scriptable browser looks even uglier than your original design, so you've lost the whole point.

Using PHP to manipulate visuals is definitely not the way to go, PHP is meant for server side processing, and you shouldn't be using any logic to handle client devices (screens) or rely on results from a script (which is a bad idea for reasons mentioned above).

If CSS can't do it for you now, write some client side script that only *enhances* the experience by resizing elements for narrow displays, but make sure it still *works* (i.e, the page looks decent) when scripting is not available.

---

