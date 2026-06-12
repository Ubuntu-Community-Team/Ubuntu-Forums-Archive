---
title: "Easy to use drawing tablet"
date: 2021-08-21
forum: New to Ubuntu
---

### Post by nginmu on 2021-08-21
I post quite a bit in an electronics design forum, very often there's a need to just sketch a quick circuit diagram and post it to the forum as an image file.

Generally such diagrams are black and white and consist of mainly straight lines, simple line-art component symbols and handwriting.

I've been trying all sorts of solutions like Gimp, snapping pics of hand-drawn diagrams with a mobile phone, trying to use a webcam, various online sketching sites etc

All have been much fiddlier and slower solutions than I've really wanted.

Easiest method I've settled on so far is to sketch my diagram on paper, and then get Mrs Nginmu to photograph it on her phone and message it to me on Facebook.

So I was looking at drawing pad devices, this brand in particular: [https://www.xp-pen.com/](https://www.xp-pen.com/)

These claim to have support for Linux, so I thought something like that might be really easy to use (especially if I could use it by placing a sheet of plain A4 on top & just drawing with a regular biro) if I could just press a button and have a .png image sent straight to the desktop.

Does anyone have one of these devices and know if it's likely to work on Lubuntu?

Or is there anything better, simpler, more Linux-friendly anyone could recommend for the purpose?

Massively high resolution, maximal range of colours etc. aren't a priority. Ease and speed of use are.

---

### Post by guiverc on 2021-08-21
I QA-test and use various devices, one is a *tablet computer*
```
- motion computing j3400 (c2d-u9400, 4gb, intel mobile 4 series)
```

It has a wacom pen that has the effect of moving the pointer around like it's a mouse (the pen doesn't need to touch the screen, just be close). The pen has a button that works like mouse click.

 It works in Lubuntu like any other GNU/Linux I've use.  If I needed to do a sketch, that device would be my *goto*, as I've played with it using Krita, and the output is really just limited by my **inability** to draw.

For that device nothing was required to be done, the pen works using all *Lubuntu* (including *live*) since 18.04 (I started QA-testing in the *cosmic* or 18.10 cycle so have tested a number of 18.04 *respins*). I'd hope you'd get the same for most, if not all, devices plugged in, but sorry I don't know.

---

### Post by Holger_Gehrke on 2021-08-21
Most - if not all - graphics tablets are not pressure sensitive at all. The pressure sensor is in the pen so you can forget about the idea of using a biro on such a device. I've got a cheap tablet from ALDI (discount supermarket chain that often has non-food special offers) which is pretty much plug-and-play. For quick sketches I wouldn't use GiMP or Krita. I actually use MyPaint with it and it works quite nicely, although I - like guiverc - couldn't draw my way out of a paper bag ...
On the other hand, there are specialized programs for drawing circuits - kicad comes to mind - and there are symbol sets for drawing circuits available for Inkscape. Using either of those will produce better looking drawings then doing them by hand on a tablet.

Holger

---

### Post by nginmu on 2021-08-21
That's what I'm trying to get away from, getting involved in complicated / specialised packages. I know of a whole bunch & they never seem to let me draw what I want to draw. I just want to draw some few lines on a flat surface, press a button, and get an image file - nice and simple and quick. Generally nothing more than 5 or 6 lines and a handful of resistor / capacitor / transistor etc symbols.

Yes I can see now, looking at what's on offer on the web, that hoping to avoid the use of a dedicated pen is a trouble - but that's ok, having a 'real' paper copy and being able to use any pen isn't that important. Pressure sensitivity isn't too important, the presence or absence of a line is generally sufficient, but all the same if it's easier just to accept using the pen that's part of the device that's ok.

I did come across an ALDI device during my searches, "Medion P82001 Digital Notepad", is that the same as what you've got? If it is, and you've found it's ok, I'll get one!

I was also looking at a standalone pen which digitises whatever you write, "Logitech IO Personal Digital Pen" & also "IO2". Looked pretty Windows-only though.

I'm sure I've got an old Tesco Hudl lying around somewhere.. talking about the motion computing j3400 made me wonder if I could do something with that. Hmm..

---

### Post by Holger_Gehrke on 2021-08-22
No, what I've got is a 'Perixx Peritab 301'. That's a rebranded Waltop tablet according to its USB ID. It's more or less compatible with a Wacom tablet. Might not have been from ALDI after all, ALDI computer hardware is usually branded Medion. I got it from a flea market years ago for a few Euros. It's old enough that it prominently mentions compatibility with Windows Vista on it's packaging ...

That P82001 seems interesting. According to the [manual for it that I found on manualslib]("https://www.manualslib.de/manual/467843/Medion-P82001.html#manual") it's a stand alone device which will store up to 99 pages of notes/drawings internally or on SD-Card or work as a graphics tablet if connected to a computer. It also has a pen which can take tips that actually do write on paper, so this seems good. Sadly the manual also mentions the need for a converter - which is included only in a version for Windows - to use the drawings stored on the tablet on a PC. According to [this page]("https://www.linuxquestions.org/questions/linux-software-2/wanted-program-to-open-convert-waltop-top-files-687959/") there is a converter that should work on Linux. Also it runs on five AAA batteries (four in the tablet, one in the pen) for about 20 hours in stand alone mode - not too good.

Regarding that Tesco Hudl: that's an Android Tablet with Android 4.2, isn't it ? There are some more or less hacky ways of using an android tablet as a graphics tablet or you could try to use one of the many drawing apps for android on it. In both cases it's more like finger painting than drawing unless you have a stylus that works with the touchscreen.

Holger

---

### Post by nginmu on 2021-08-23
I'll give KiCad a try as soon as I can get it to install - it actually looks very good - Having a few problems with Muon at the mo though. I've asked about that on a separate thread.

---

