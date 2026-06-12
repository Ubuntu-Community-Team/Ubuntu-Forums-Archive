---
title: "define margin using pixels or percent?"
date: 2012-11-12
forum: Programming Talk
---

### Post by chuchi on 2012-11-12
Hi there! This is my question.
 

 Let's say I have two divs, div1 and div2. To define the top margin of div2 respect div1, I can do it in two ways using css.
 

 top:20px;
 margin-top:2%;
 

 What's the best way to do it?? I am sorry because I know this is a stupid question, but I want to know the main differences between those two ways.
 

 Thanks a lot!

---

### Post by trent.josephsen on 2012-11-12
Those actually do quite different things. **top** is only meaningful for an explicitly positioned element, and it means different things according to whether you use relative, absolute or fixed positioning. **margin** on the other hand controls the size of the element's margin, which not only affects its position on the page but also changes how inline elements flow around it. Top and bottom margins of consecutive elements can also be collapsed, so if you have two consecutive <div>s with 10px top and bottom margins, the margin between them will be 10px, not 20px.

You've also changed the way you specify values -- your positioning is defined in terms of pixels but your margin in a fraction of the containing element. You could do the opposite if you wanted, and which choice is right for a particular case is, again, dependent on the rest of the layout. I can think of cases where both would be useful.

EDIT FOR DISCLAIMER -- I am a hardware engineer and my forays into Web design are amateurish. This post does not constitute a professional opinion.

---

### Post by chuchi on 2012-11-13
Hi! thanks for reply! I think I have understood your idea, but not completely. Given this code:

```

<!DOCTYPE html>
<html>
    <head><title></title>
<style> 

#main_div
{
    width: 80%;
    position: relative;
    height: 600px;
    background-color: orange;
    
}
#div_1
{
    position: relative;
    left: 200px;
    margin-top: 2%;
    border: 2px solid black;
    width:100px;
    height: 100px;
    background-color: yellow;
}
</style>
</head>
<body>
    <div id="main_div">
        <div id="div_1">this is div_1</div>
    </div>
    
</body>
</html>

```

I have a main div(main_div),  and another div inside "div_1" . If I change the margin-top value of div_1, the main_div is also moved, why??

---

### Post by trent.josephsen on 2012-11-13
I haven't tested to be sure, but I would guess that's because of the "collapsing" effect I mentioned before. In this case it's the top margin of #main_div collapsing with the top margin of #div_1, so the larger value is used. If this is undesirable, you can defeat it by putting another element (with something invisible in it, e.g. a transparent "spacer" image or text the same color as the background) at the top of #main_div, before #div_1, so the margins aren't next to each other. Or you can position the element and move it down with **top** instead.

Margins are essentially for controlling the whitespace around an element. If you want 10pt white space around paragraphs, and 20pt white space around figures, you don't add them to get 30pt when you have an figure followed by a paragraph; you use the larger value. That's why margins collapse the way they do.

---

### Post by kevinharper on 2012-11-13
[https://developer.mozilla.org/en-US/docs/CSS/CSS_Reference](https://developer.mozilla.org/en-US/docs/CSS/CSS_Reference)

Scroll down to "M". Everything you need to know about margins.

---

