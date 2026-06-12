---
title: "How To: Watch QuickTime Videos in Linux"
date: 2008-08-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Exsecrabilus on 2008-08-01
I recently learned of a fantastic simple way to watch QuickTime videos from [_this blog post_](http://linux-blog.org/index.php?/archives/273-Apple-Denies-Linux-Access-To-Its-Movie-Trailers.html). I thank that guy so much.

OK, so that blogger already explained how to do it, so what's this for? Well, I have nothing else to do and I guess I will give more detailed instructions for brand-new Linux users who don't know how to do anything.

Here are the steps:


[LIST=1]
[*]Find a video that will prompt you the installation of QuickTime. (We'll use this [_WALL-E movie trailer_](http://www.apple.com/trailers/disney/walle/trailer_medium.html) from Apple for this How To.) 


[*]Stay on the page of the trailer, and press Ctrl+U. A new window should pop up with a bunch of text of different colors. Don't worry about it, just don't close it.


[*]Now press Ctrl+F and in the typebox that just appeared on the bottom left, type in ".mov" (without the quotes.) The page should instantly scroll down by itself and you should see a full http link with ".mov" highlighted. Highlight the whole link (example: _[http://movies.apple.com/movies/disney/wall-e/wall-e-tlr3_h.320.mov](http://movies.apple.com/movies/disney/wall-e/wall-e-tlr3_h.320.mov)_ ) and press Ctrl+C.


[*]**Not Preferred. See Below.** To watch it in your web browser, open a new tab/window and click on the address bar; then press Ctrl+V. The page should turn black with the text *(no video)* in the middle. Do not worry, wait a few seconds and the video will start. You might notice, however, the video will look stretched. Try the next step for better results.


[*]To download it and watch it with your preferred video player with the trailer's intended resolution (plus no buffering) use this method. Goto *Applications -> Accessories -> Terminal*. Type in "wget" (without the quotes) and press Space (on your keyboard.) Then right-click and click Paste. Using my demo video, it should be:
```
<username>@<Computer>:~$ wget http://movies.apple.com/movies/disney/wall-e/wall-e-tlr3_h.320.mov
```
Press Enter and when it finishes, goto *Places -> Home Folder*. Double-click on the video and watch it.
[/LIST]

---

