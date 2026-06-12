---
title: "Javascript and window size"
date: 2006-03-20
forum: Programming Talk
---

### Post by unkemptwolf on 2006-03-20
Alright, so I've got this script to create a slideshow of images. The problem is that I want it to stretch across the whole page, but I cant get firefox to tell me the actual size of the area I have to work with (i.e. the width of the document not counting scroll bars, edges, etc.). I'm new to javascript, so I'm sure this is simple. It works fine in IE, it just wont work in anything else! I'm currently using window.innerWidth to get the size of the screen, but that doesnt take into account whether the scroll bar is there or not, and its very important that I use as much screen real estate as possible, without turning on the bottom scroll bar.

As a last resort, is there anyway to tell if the scroll bar is on for the current page, and subtract its width manually?

---

