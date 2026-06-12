---
title: "ActionScrip 3.0 question."
date: 2010-12-25
forum: Programming Talk
---

### Post by AbsolutCommando on 2010-12-25
I am building a flash website for a friend and I have managed to load an external .swf file to the .fla project. My problem is, that when I test the movie out, I can't manage to remove the .swf file at the click of a button. For example, if button 3 is clicked, it should show the picture gallery, and when the user clicks button 4, the picture gallery should disappear. I am very new to AS 3.0 and flash itself, anyone have any suggestions?
BTW, here's my code:

[COLOR=Red]stop();
    function button1_clicked(e:MouseEvent): void    {
    gotoAndStop("page1");
}
    function button2_clicked(e:MouseEvent): void    {
    gotoAndStop("page2");
}
    function imagegallery2_clicked(e:MouseEvent): void    {
    gotoAndStop("page3");
}
    function button4_clicked(e:MouseEvent): void    {
    gotoAndStop("page4");
}
/////////////////////////////EVENT LISTENERS//////////////////////////////////
button1.addEventListener(MouseEvent.CLICK, button1_clicked);
button2.addEventListener(MouseEvent.CLICK, button2_clicked);
imagegallery2.addEventListener(MouseEvent.CLICK, imagegallery2_clicked);
button4.addEventListener(MouseEvent.CLICK, button4_clicked);

/////////////////////////////EMBED SWF///////////////////////////////////[/COLOR] [COLOR=Red]
var Xpos:Number = 402;
var Ypos:Number = 203;
var swf:MovieClip;
var loader:Loader = new Loader();

var defaultSWF:URLRequest = new URLRequest("swffolder/imagegallery2.swf");[/COLOR] [COLOR=Red]
loader.load(defaultSWF);
loader.x = Xpos;
loader.y = Ypos;
addChild(loader)[/COLOR]

Another question, I have a box on the main site, how would I resize the .swf to fit the box on the site so it doesn't overlap?

---

### Post by skullmunky on 2010-12-29
I think it's because the movieclip you've loaded exists throughout the root timeline, not just at the "page3" frame.  the method you're using works well if you build your movieclips within the flash document and put them in the specific frames of your timeline, but I don't think it works as well with dynamic loading.  try changing the visibility of the mc instead of jumping to frames.

---

