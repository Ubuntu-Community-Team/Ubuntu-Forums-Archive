---
title: "Who knows Flash?"
date: 2009-12-14
forum: Programming Talk
---

### Post by cartisdm on 2009-12-14
Situation:

My boss wants me to help out on a project he and some other guys have been working on but haven't had any luck.  I'm kind of getting thrown balls deep right in the middle of the project so forgive my lack of knowledge on everything at the moment.

I don't have ANY experience with Flash or Flash players or anything of that nature really but he's created a website that that he wants to embed a flash player that will have some videos load depending on the options selected by the user.

Questions:

- Is it better to use a pre-made flash player and embed that on the site or create one in Flash?
- The videos are high quality .mov (approx. 1GB and 15 min.) files and the quality needs to be preserved to the best possible while still getting fast load times
- Do I convert/compress the video files in Flash or what do you suggest?
- Any other suggestions?

Like I said, I'm kind of getting thrown into the middle of all this because my boss has gotten annoyed that the project is taking longer than he expected and he thinks I'll be able to help....](*,)

---

### Post by shadylookin on 2009-12-14
> **cartisdm said:**
> Situation:

My boss wants me to help out on a project he and some other guys have been working on but haven't had any luck.  I'm kind of getting thrown balls deep right in the middle of the project so forgive my lack of knowledge on everything at the moment.

I don't have ANY experience with Flash or Flash players or anything of that nature really but he's created a website that that he wants to embed a flash player that will have some videos load depending on the options selected by the user.

Questions:

- Is it better to use a pre-made flash player and embed that on the site or create one in Flash?
- The videos are high quality .mov (approx. 1GB and 15 min.) files and the quality needs to be preserved to the best possible while still getting fast load times
- Do I convert/compress the video files in Flash or what do you suggest?
- Any other suggestions?

Like I said, I'm kind of getting thrown into the middle of all this because my boss has gotten annoyed that the project is taking longer than he expected and he thinks I'll be able to help....](*,)


I assume you want something like youtube where you watch videos? Because Flash player actually means the client software that runs .swf files. 

I'm pretty sure there's a way to just import a movie file if you're using Adobe Flash to make it.


If I were you I'd just host the videos on youtube and use an html page to let the user select which one to watch.

---

### Post by jollysnowman on 2009-12-14
> **cartisdm said:**
> - The videos are high quality .mov (approx. 1GB and 15 min.) files and the quality needs to be preserved to the best possible while still getting fast load times

Can you use HTML5 instead? flash, fast load time, and quality are not really mutually related.

---

### Post by cartisdm on 2009-12-15
> **jollysnowman said:**
> Can you use HTML5 instead? flash, fast load time, and quality are not really mutually related.

As far as I know there is no requirement of using Flash.  What would I need to look into for using HTML5? (to be honest, never even heard of it)

EDIT: Scratch that, I had a brain fart and thought HTML5 was a video format.  Regardless, how would I go about using a video player that worked in HTML5?

---

### Post by JLinden on 2009-12-15
I think it's to early to use HTML5 for a serious project. Not enough browsers support it, at least not full support. On the other side, it's a great initiative to use HTML5, and help bring the development forward, and push the browsers into HTML5-support.

Check this out: [http://www.w3schools.com/html5/tag_video.asp](http://www.w3schools.com/html5/tag_video.asp)

---

### Post by Marlonsm on 2009-12-15
It's not time for HTML 5 yet. Remember IE doesn't even know what it is.

But Adobe Flash does have some "pre-made" vide players, which are very easy to set up. In Flash 8 (the one I used) it was just a matter of following the instructions.

---

### Post by ve4cib on 2009-12-15
Just a thought, but rather then trying to stream 1GB video files with Flash is it possible to just provide a link to download the file so the user can watch it locally?

```
Click <a href="resources/videos/hires/the-video.mp4">here</a> to download our video demo
```

When the user clicks on the link they'll be prompted by their browser to either open the file with an external program, or save it.  Possibly, if they have a video player plugin (like those provided by VLC or Mplayer) they could watch the video in the browser with the plugin.  It's not *as* pretty, but it's a whole lot easier to code.

Alternatively, you could even compress the file into a .zip (or similar), forcing the user to download it, extract it, and watch it locally.  It's less convenient but saves on bandwidth and server storage space.

---

### Post by cartisdm on 2009-12-15
Ok, so it sounds like the HTML5 idea is a no-go from what you all are saying about it.  I can't have the user download it locally because he has a specific layout on his site and it has to load in the window (it's a project for a research grant so he's extra picky).

What should I look into for getting a quick loading stream? Is most of what makes quick video streaming done by the compression of the video or are there other common factors that are considered?

---

### Post by cartisdm on 2009-12-16
in addition to my post right above this one (I'm making a new post in an effort to bump the thread), am I even going about loading these videos in the most efficient mannor?

I'm reading through a Flash book and it keeps mentioning Flash Media Server.  Is this literally a server that I can use to host my media? Right now we have an account with IPower and they are hosting our website so we're just using that same server to host the .flv files and stream them from there.  Would this cause poor streaming ability?

---

