---
title: "HTML, CSS, no JAVA: Product box, how to?"
date: 2013-04-04
forum: Programming Talk
---

### Post by zero2xiii on 2013-04-04
Hay all,

I am having a trouble with this little thing. I am a complete newbie to website programing, designing and so forth.

I want a dialog box, or what ever you wish to call it similar to the one on chauvet's website:
[http://www.chauvetlighting.com/4-bar-tri.html](http://www.chauvetlighting.com/4-bar-tri.html)

It is the little box on the right hand side with the three tabs: Feature, Spesifications, Resources.
Moving your mouse over each tab changes the box's content, without loading anything extra. Viewing the page source I found this:
```
<div id="product_tabs" class="producttab1">
    <div id="tab1" onmouseover="changeTab(1);"><p><a href="#Features" onclick="return false;">Features</a></p></div>
    <div id="tab2" onmouseover="changeTab(2);"><p><a href="#Specifications" onclick="return false;">Specifications</a></p></div>
    <div id="tab3" onmouseover="changeTab(3);"><p><a href="#Resources" onclick="return false;">Resources</a></p></div>
    <div class="clear"></div>
</div>
    <div class="clear"></div>
<div class="product_box" id="content1">
    <div class="textpadding"><ul>
<li>Complete, portable LED wash lighting solution with high-intensity, tri-color LEDs </li>
<li>Four, individually-focusable heads allow total room or stage coverage</li>
<li>Low-profile lights are 1.6in deep and can fit in almost environment </li>
<li>Set-up and teardown in minutes with the included tripod, carry bags, and footswitch</li>
<li>High-powered, tri-colored LEDs nearly eliminate multi-colored shadows </li>
<li>Safely mount to truss using the built-in bolts for increased flexibility and mounting options </li>
<li>Works in master/slave with other <a href="\&quot;http:/www.chauvetlighting.com/4-bar.html\&quot;" target="\&quot;_blank\&quot;">4BAR&trade;</a> and <a href="\&quot;http:/www.chauvetlighting.com/4-bar-tri.html\&quot;" target="\&quot;_blank\&quot;">4BAR&trade; Tri</a> units for large coordinated light shows</li>
<li>Power link up to 8 units which saves time running cables and extension cords</li>
<li>Sound-activated programs dance to the beat of the music</li>
<li>Easy-access to built-in automated programs generate a synchronized show in master/slave mode</li>
</ul></div>
</div><!--product_box content1-->

<div class="product_box_hidden" id="content2">
    <div class="textpadding"><p>&bull; DMX channels: 15<br />&bull; DMX connectors: 3-pin<br />&bull; Light source: 28 3 W (350 mA x3) tri-color LEDs 50,000 hrs<br />&bull; Stand height: 56 - 91 in<br />&bull; Beam angle: 22&deg;<br />&bull; Field angle: 42&deg;<br />&bull; Illuminance: 1,869 @ 2 m (per pod)<br />&bull; Power linking: 8 units @ 120 V / 16 units @ 230 V<br />&bull; Input voltage: Auto-ranging 100-240 VAC 50/60 Hz<br />&bull; Power and current: 113 W, 1 A @ 120 V 60 Hz<br />&bull; Power and current: 118 W, 0.5 A @ 230 V 50 Hz<br />&bull; Weight: 31 lbs (14.1 kg)<br />&bull; Size: 48 x 2.2 x 11.2 in (1,219 x 55 x 285 mm)<br />&bull; Approvals: CE</p></div>
</div>
<!--product_box content1-->

<div class="product_box_hidden" id="content3">
    <div class="textpadding">
      <p><ul>
<li><strong>Product Specification Sheet</strong><br /><a href="/products/spec/4BarTRI-CutSheet.pdf" target="_blank" title="">4BarTRI-CutSheet.pdf (1172K)</a><br /><br /></li>
<li><strong>User Manual</strong><br /><a href="/products/manuals/4BAR_Tri_UM_Rev2_WO.pdf" target="_blank" title="">4BAR_Tri_UM_Rev2_WO.pdf (1181K)</a><br /><br /></li>
<li><strong>Quick Reference Guide - multi-language</strong><br /><a href="/products/manuals/4BAR_Tri_QRG_ML_Rev2_WO.pdf" target="_blank" title="">4BAR_Tri_QRG_ML_Rev2_WO.pdf (1144K)</a><br /><br /></li>
<li><strong>ShowXpress Profile</strong><br /><a href="/products/showxpress/4BAR_TRI.zip" target="_blank" title="">4BAR_TRI.zip (0K)</a><br /><br /></li>
</ul></p>
    </div>

```

Viewing the CSS style sheet made my head ache:
```
#product_tabs { width: 274px; height: 22px; position: relative; }
.producttab1 { background: url(/images/product_tabs.gif) 0px 0px no-repeat; }
.producttab2 { background: url(/images/product_tabs.gif) 0px -22px no-repeat; }
.producttab3 { background: url(/images/product_tabs.gif) 0px -44px no-repeat; }
#product_tabs p { margin: 0; padding: 0; }
#product_tabs p a { text-decoration: none; color: #fff; }
#product_tabs div { float: left; position: absolute; top: 3px; }
#tab1 { left: 15px; }
#tab2 { left: 93px; }
#tab3 { left: 197px; }

.product_box { width: 272px; background: #707173; border: 1px solid #5c5c5c; border-top: none; border-bottom: none; display: block; }
.product_box_hidden { display: none; }
.textpadding { margin: 0 15px; padding-top: 10px; word-wrap: break-word;} /* amir added CSS3 property word-wrap */
```

I THINK this is all the source code needed for that little box thingy, however I can't make heads or tails on how to rewrite this for my website? I do not want to EXACTLY copy this. So I need a frame work on how to code it so I can add tabs if needed, maybe even add some images inside the tabbed-content, etc.

Even just copy pasting the above to a blank page and style sheet the effect is not working. So I am having a really hard time figuring out what makes this tick. Again I do not wish to just copy chauvet's code on this, I merely want a similar effect I can modify for my purposes.

Thank you in advance.

---

### Post by ofnuts on 2013-04-04
There is a changeTab() Javascript function called when the mouse is over the tab... (in other words, you haven't got the whole source).

---

### Post by zero2xiii on 2013-04-04
So,

There is no way to replicate it without java? Because I prefer not to use java for such a very basic website as this is intended to be.
Or even doing something similar? Maybe 3 pages, even if you have to click on a "tab" to change the content?

Cheers

---

### Post by r-senior on 2013-04-04
That box is done with JavaScript, not Java. It doesn't need a Java plugin, just JavaScript enabled in the browser.

It's this section of code:

```
<script type="text/javascript">
function changeTab (n) {
document.getElementById('product_tabs').className = 'producttab'+n;
if (n==1) {
document.getElementById('content1').className = 'product_box';
document.getElementById('content2').className = 'product_box_hidden';
document.getElementById('content3').className = 'product_box_hidden';
}
if (n==2) {
document.getElementById('content1').className = 'product_box_hidden';
document.getElementById('content2').className = 'product_box';
document.getElementById('content3').className = 'product_box_hidden';
}
if (n==3) {
document.getElementById('content1').className = 'product_box_hidden';
document.getElementById('content2').className = 'product_box_hidden';
document.getElementById('content3').className = 'product_box';
}

}
</script>

```

Then the divs with ids content1, content2 and content3 are defined immediately below. That's what your listing shows.

You can't do this sort of document model manipulation without JavaScript using HTML4. I'm not sure if HTML5 can do it -- somebody else might know that.

---

### Post by ofnuts on 2013-04-04
I said *JavaScript*, not *Java*. These are two different languages with two very different impact on web pages. JavaScript is about unavoidable in modern web pages, but Java applets are getting rare.

---

### Post by r-senior on 2013-04-04
> **ofnuts said:**
> JavaScript is about unavoidable in modern web pages, but Java applets are getting rare.
+1

Lots of advisories these days suggest disabling the plugin that runs Java applets.

---

### Post by zero2xiii on 2013-04-04
Hay,

Sorry about the Java vs Java Script thing. As I said, I am a novice at html and web elements. I do bash scripting mostly... and even that is rare..

Anyway. So i must use the java script. Ok, but how then do I create such a "box"?

Let me start with the basics.

I assume I need to put this java script code somewhere, in a file similar to the css data? And then from there I need to create the layout inside a CSS template/style? And after that, I need to call these two elements from within the page, and add content to it via the normal <p> tags (if they are called tags anyway).

Thanks for the help so far, at least now I know java script is a must.

---

### Post by ofnuts on 2013-04-04
The way it is done in the page you refer to: they define two styles in the CSS file (productbox and productbox_hidden) and assign them dynamically to the elements to hide/show. For that specific case, it"s a bit of overkill, the visibility can be toggled directly without changing the style. But this technique has its merits in more complex designs.

The Javascript code can be in a separate file or directly in the HTML page (like CSS...).

---

