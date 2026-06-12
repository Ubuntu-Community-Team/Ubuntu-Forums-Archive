---
title: "web browser doesn't show everything"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by dori321 on 2012-11-13
Hi!

I installed ubuntu in my laptop.
When I use a browser in hebrew websites (doesn't matter which one - for this example it's firefox), some of the text doesn't appear - it's seems that there is not enough space for all the text. Probably you didn't understand what I meant so I added 2 attachments with a capture of windows and linux using firefox. There are red rectangles of text that appears in windows but it doesn't in linux.

Anybody knows how to fix this problem? It really bothers me and makes me switch back again to windows.

I didn't change any fonts size, only installed hebrew support.

Thank you,
              Dori

---

### Post by greatsirkain on 2012-11-13
try zooming out? (ctrl- to zoom out ctrl+ to zoom in)

---

### Post by mardybear on 2012-11-13
Hi dori321.

In addition to zoom, Firefox also has various font choices, including font size. You can set a minimum font size and should also be able to select something like zoom only text/not full page or images. Any help?

mardybear

---

### Post by dori321 on 2012-11-13
I don't think that zoom is the solution because it won't change the location or the words or the font size.
About the font size, it strange because in the both firefox the font size is the same, the only different is the space between the word, but I'll try it. Hope it won't cause any other problem in other sites.

---

### Post by mardybear on 2012-11-13
Hi again dori321.

I'm using a different version of Ubuntu (old 8.04). In my package manager, synaptic, i have numerous Firefox language packs, including mozilla-firefox-locale-he-il, the Mozilla Firefox Hebrew language/region package.

If you don't have the synaptic package manager, it can easily be installed by using the terminal (in your version i believe it opens with ctrl-alt-t or similar combo) via the command 'sudo apt-get install synaptic' and later run/opened via terminal by typing 'gksudo synaptic'.

Close Firefox if still open and install the Hebrew language package via synaptic. Open synaptic and select 'all' from the left pane, click the 'search' button and search for Firefox or Hebrew. Right click to select the package you want to install, select 'mark for installation' and then hit 'apply' at the top of the synaptic package manager. Wait for the install to complete, reopen Firefox and see if it's any better.

mardybear

---

### Post by quentinl on 2012-11-13
try making the text size smaller in edit>preferences

---

### Post by dori321 on 2012-11-14
I try to zoom, but nothing good happens (all the page become smaller).
I also tried to change the font size, but no success - the font still the same size as it was (though I uncheck the option that let the page decide the font's size). But I thought it won't work because the web has different fonts with different size.

I tried to install chrome and the page looks the same as firefox (on unbuntu) so probably something the the fonts of linux...

---

### Post by lovevn on 2013-01-20
Hi everyone!
I have a same problem. I installed completely Ubuntu 12.04. My firefox 18 doesn't display some Vietnamese website, example, quantrimang.com.vn or thongtincongnghe.com. It shows like this:

[IMG]http://nu8.upanh.com/b6.s33.d2/ce1590a684b5e3d7cdacb6d1808e9810_52735608.fferr.png[/IMG]

[IMG]http://nu0.upanh.com/b4.s34.d1/53599915575be03d7e0ac593f2d4c137_52735610.ttcn.png[/IMG]

when I enter that website, it displays text when firefox's loading site, but when it loads completely, there is nothing like that. Google Chrome doesn't have that problem!
I think perhaps firefox has some problem whith fonts, but I don't know how to fix.
I try install ttf-mscorefont and type
```
sudo fc-cache -fv
```
(but I don't copy font from windows to Ubuntu!)
but it didn't change!
Pleased help me!

---

