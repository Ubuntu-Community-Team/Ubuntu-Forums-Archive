---
title: "How can a website slow down the speed of the web browser?"
date: 2010-06-05
forum: Programming Talk
---

### Post by hockey97 on 2010-06-05
Hi, I am working on a website. I would like to know how a website can slow down the web browser. 

I know the more content you have the slower it loads onto the clients web browser.

I would like to know if you you reduce the content that gets loaded first and later on when other content is needed that you can load that in later. Would this be the best way to manage a website with alot of content? 

My idea right now is to load the important content first and later on based on events other content can get loaded into the site.

My question would be would this best way to now have the web browser slow down. 

I was told the reason the web browsers slow down when loading a website is based on what is being loaded first and if that website loads in alot of content at one way meaning on the main page then there will be a loading time meaning it will slow down the browser.

I want to know if it's a good idea to load in the extra content only when it's needed and when it's not needed to unload them?

I am making a website with alot of content in it but want to keep it light weight as possible. So it's not a load for the web browser causing the slow down when viewing the website.

---

### Post by nvteighen on 2010-06-05
Ugh... if you notice an important browser slowdown when loading your page, then it sounds that you're page is badly designed... or that you should break the content in several pages... Hey, this is the Internet, it's quite normal to split content through several pages to aid navigation. 

(Another possibility, but only valid if you're testing your server from the outside, i.e. not from localhost, is that you don't have enough bandwidth)

But, if you persist on your idea, well... first of all, the slowdown should be done from the server-side. Client-side is absurd because you'll have to load the whole thing anyway in order to make the browser do its part locally. No, it'll have to be done from the server... something like hiding the amount of content you feed the user's browsers until the user asks for more or some condition is met. Not being a web developer at all, I'm sure something like that can be done.

---

### Post by shadylookin on 2010-06-05
You should just use javascript and html DOM to create dynamic pages that respond to user interaction. 

You should never try to slow down the browser. That's just going to make for a lot of unhappy people and it's not really a solution to anything.

---

### Post by hockey97 on 2010-06-05
Ok, I am not trying to slow down the web browsers on purpose. 

My internet is a business line it's good and there isn't any bandwidth hog.

There isn't a currently problem causing a slow down on Internet browsers.

I am trying to deal which such a problem if it occurs at any point.

I currently use ajax with javascript. 

I have a design a page that is the clients accounts page. This page has alot of apps that use ajax talking with php to load when a condition is met in this case once a person clicks a image it will run a function which would use ajax and run a php script to grabe content or do something special.

I plan to keep adding on to features causing at some point where there will be too much content. 

The main reason I ask this question is that I have a area where once you click a image it will load in images of items of the user that wanted to buy these items etc. I want to know if there is like 500 images I know you would use a php paging system. But I was woundering if I can make a javascript that detects a scroll up or down that it will first only load in 10 images and if it scrolls down a few images it will the load the next 10 images and keep doing this. I want to know if I load 10 at a time as the user scrolls downwards and at the end they load 500 images total but not at the same time would this slow down their web browser or computer any?

I plan to load 10 images more every time the person scrolls down 3 or 5 images down. 

I want to use a ajax way to load stuff in rather then have a paging system with php where you have to click links and the paging system.

I want to use something like a paging system but by using ajax but not using links in other words when the person scrolls it will load more images.

But I was thinking if I load 10 more should I find a way to also unload the images already view and is up passed the scroll meaning it's now being viewed currently.

---

### Post by soltanis on 2010-06-05
Don't worry about making browsers slow. If there is a lot of content on one page, then there's a lot of content on one page; any browser worth its beans will load it intelligently from your server. If you're going to display a lot of images on one page, then to cut down on server-side load, you should present them in some kind of thumbnailed format (there are a lot of libraries to do this for you) that gives a low-res version of the picture, and when people click on it, they can see the high-res (and large sized) picture. JPEG and PNG are your friends, obviously.

And also don't worry about the browser's ability to allocate and free memory. On any system made in the last 10 years this is barely noticed by the user. The only case where you should be concerned with this is mobile devices (i.e. cell phones, iPads). In this case, my suggestion is thumbnail aggressively, use a mobile version of the page that presents less images at once, and try to model your UI the same way those devices do (i.e. don't put everything on one wide and tall page, break it up into much smaller cards that these tiny-screened devices can more easily view...and manage in memory).

---

### Post by dtfinch on 2010-06-05
A couple things to avoid delays in page rendering after the html has loaded:
1. Always specify width and height in image tags. If you omit them, some browsers postpone displaying the page until it's loaded enough to know their dimensions, to avoid excess relayouts as the page is loading.
2. Move external script tags to the bottom of the page whenever feasible. Anything below a script tag isn't rendered until the external script has been downloaded and executed. This isn't so much of a problem on scripts that are cached after the first load, unless the server tells it to always revalidate, but it's a huge problem on sites with banner ads loading as external scripts. Especially if the ad server stops responding, the user could be stuck with a blank page for a minute or two even though the entire rest of the page has been downloaded.

---

### Post by juancarlospaco on 2010-06-05
*This can be done but not from programming side...*

---

