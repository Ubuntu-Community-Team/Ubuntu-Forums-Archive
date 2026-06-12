---
title: "[SOLVED] CSS absolute positioning"
date: 2009-01-04
forum: Programming Talk
---

### Post by mohtasham1983 on 2009-01-04
Hi,

I have a div element, that is located on the right side of my page. The content of this div element is made using AJAX. So after my page is loaded, When I click on the video button on the left side of it, it shows a list of all videos inside my container. What I want is when i click on each item on the list, a flash video player pops out in the center of the page. 

I'm following the flowplayer website tutorial, and trying to achieve something similar to this one:
[http://flowplayer.org/demos/overlay.htm](http://flowplayer.org/demos/overlay.htm)

As you can see, when you click on any of the buttons. a flash player appears on the page on top of a white background. The jquery overlay plugin takes care of positioning the white background in the center of the page for me, but since my actual video player, whose display setting is set to none, is inside my div container(On the right), jquery overlay plugin places my flash player out of the screen on the right side.

It automatically finds how much the left attribute should be based on the screen size and places the white background correctly. It sets the same left size for my video player, but it places it relative to my div container even though firebug shows that the position is set to absolute for my player. I used some trick to override this left value and set it to zero, so that it still appears at least on my page. However, it's very ugly and not on top of the white background.

Does anybody know how I can set the position attribute of my player, absolute to the body of my document and not that of its parent container?

Thanks in advance.

---

### Post by Mickeysofine1972 on 2009-01-04
The best way is to put this div before any of the main page div and mak it display: none;

That way there is no inheritance of any positioning other than the body, which I think is what you want.

Mike

> **mohtasham1983 said:**
> Hi,

I have a div element, that is located on the right side of my page. The content of this div element is made using AJAX. So after my page is loaded, When I click on the video button on the left side of it, it shows a list of all videos inside my container. What I want is when i click on each item on the list, a flash video player pops out in the center of the page. 

I'm following the flowplayer website tutorial, and trying to achieve something similar to this one:
[http://flowplayer.org/demos/overlay.htm](http://flowplayer.org/demos/overlay.htm)

As you can see, when you click on any of the buttons. a flash player appears on the page on top of a white background. The jquery overlay plugin takes care of positioning the white background in the center of the page for me, but since my actual video player, whose display setting is set to none, is inside my div container(On the right), jquery overlay plugin places my flash player out of the screen on the right side.

It automatically finds how much the left attribute should be based on the screen size and places the white background correctly. It sets the same left size for my video player, but it places it relative to my div container even though firebug shows that the position is set to absolute for my player. I used some trick to override this left value and set it to zero, so that it still appears at least on my page. However, it's very ugly and not on top of the white background.

Does anybody know how I can set the position attribute of my player, absolute to the body of my document and not that of its parent container?

Thanks in advance.

---

### Post by mohtasham1983 on 2009-01-04
Thank you for reply.

Basically, the content of my container was dynamically loaded in an AJAX call, with some div elements whose name were related to video ID. That's why, I couldn't predict them before sending the AJAX call. However, I used a trick and got it working.

What I did, was to create a div element just before </body> and set the display to none. Then when I got the content of my container successfully loaded, I moved them to the div element at the end of the page using one line of jQuery like this:

```
$('#video_player_container').appendTo($('#hidden_videos'));
```

Here video_player_container is the container, created using AJAX call and hidden_videos is the one at the end of my document.

---

