---
title: "Epson DX3800 &amp; Lexmark Z612 printers"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by iggyigg on 2008-06-06
I'm an Ubuntu novice who has never had a functioning printer with Ubuntu yet.  I have the 2 following (old!) printers and I'd like to see if you guys think that the problem is with the printers rather than with printer drivers etc with Ubuntu.  I use **Ubuntu 7.10** and the printer configurations are simply those which set up automatically.  I know nothing about downloading printer drivers but as far as I can see, this would not help......but I'd be grateful for a confirmation of that or any other advice.  My USB2 cable works fine. 
As I use Ubuntu ONLY, I can't test them on Windows any more.

[COLOR="Red"]Epson Stylus DX3800[/COLOR]
A friend of mine gave this to me, reporting (I believe) a paper feed problem.  As he's even less tech-savvy than me, I thought it worth a try under Ubuntu.  (My plan: if I can't get this one to work, then I'll buy a new one, same model, hopefully recycling cartridges from the old one!)

Under “Printer Configuration Settings”: the device URI is – **usb://EPSON/Stylus%20DX3800.**
Under “Make and Model” it's: **Epson Stylus DX3800 – CUPS + Gutenprint v5.0.1 Simplified **
Does the above look right to you?
Under “Printer State” it's “Processing”.

But the print jobs just get stored (as detailed in the document print status, when I click on the printer icon) and nothing happens.  There's clearly a communication problem!

Under the “Tests and Maintenance” heading, when I click on the options “Print a Test Page”, “Print Self-Test Page” and “Clean Print Heads”, a message says “Submitted – Test page [etc] submitted as Job [No #]”
Nothing happens thereafter and 2 small lights just continue flashing (the green power light at the top and a red one immediately under it which (judging by the paper symbol) appears to relate to a paper feed problem.

When I try scanning with X-sane 0.991, I get “Error during read. Error during device I/O.”
And the photocopier doesn't work either........:(

[COLOR="Red"]LEXMARK Z612[/COLOR]
= My old inkjet printer, I used to use on Windows which worked fine until the ink ran out. (This is my guess as it would print documents but very faintly).  In Ubuntu it refuses to do anything..... 

Under “Printer Configuration Settings”: the name is **“Z600 series”** and the type is **“CUPS Z 600 series”**. I wonder if this is specific enough, ie not to specify the EXACT model Z612?   

Under “Printer State” it stays **“Idle” **(even when I try to print).
Under the “Tests and Maintenance” heading, I can click on the option “Print a Test Page”, but the options “Print Self-Test Page” and “Clean Print Heads” are greyed out.
When I try to print a test page (under Printer Configuration – Settings tab), this message appears:
[B]“There was an error during the CUPS operation: 'client-error-document-format-not-supported'.”
[/B]
Any ideas?
And can you tell me if it's problematic (for beginners) to get printers which are a few years old to work under Ubuntu? :confused:

Thanks for any advice!

---

### Post by little_penguin on 2008-06-07
You could try using some of the drivers for other models in the DX series, to see if they work. For example, I have a DX 4050 all-in-one, but I have to use the DX 3850 driver for it to work. Good luck.

Regards,
LP

---

### Post by avtolle on 2008-06-07
Lexmarks are, at best, problematic under linux. Many Lexmark models are given the appellation of "paperweight" on the linux printing site (the link to which I've misplaced). Try a Google search, say "Lexmark Z612 Ubuntu" to see what, if anything, might be out there. Try the same search with your Epson. 

One other throught on the Lexmark; have you replaced the ink cartridge? Just a thought, as I said.

---

### Post by bumanie on 2008-06-07
The epson has a reasonable chance of working under linux, as for the lexmark, you're more likely to see a pig fly past the window.

---

