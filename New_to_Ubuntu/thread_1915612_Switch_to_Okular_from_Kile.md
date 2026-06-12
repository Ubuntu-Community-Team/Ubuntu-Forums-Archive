---
title: "Switch to Okular from Kile"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by peterson43 on 2012-01-26
I use Kile to edit my LaTeX documents and then I view them with Okular. My problem is that when I'm working from my laptop there is only room on the screen for either Kile or Okular but not both and I want to be able to switch quickly from one to the other with a keyboard shortcut. 

I know how to make keyboard shortcuts for commands like PDFLatex, ViewPDF and ForwardPDF, but none of them will do what I want. What I want is to configure ViewPDF or ForwardPDF to jump to the existing open .pdf file of the document but without opening a new window (otherwise I soon have 20 windows open in Okular of the same thing). 

If I set the ViewPDF or ForwardPDF settings to be Okular or Okular Unique it doesn't do what I want. In the Okular Unique setting it won't open up a new window, but it also doesn't switch to Okular as the active window. In the other setting it will jump to Okular as the active windonw but it will do so by opening a new window. Is there a way to get what I want out of Kile and Okular?

---

### Post by peterson43 on 2012-01-26
Okay, after posting this I finally answered my own question. In the configuration settings for the ViewPDF command, instead of Okular or Okular Unique there is another option of Embedded Viewer. If you choose this option then ViewPDF opens Okular up within Kile. This was a bit confusing to me at first since I couldn't figure out how to get back to the editing mode of Kile, but there is a button for "return to editor" at the top (shortcut for this command is Ctrl-e). 

This basically does exactly what I want. The only problem now is that I can't seem to choose the embedded viewer option for ForwardPDF (I can choose it for ForwardDVI, however). In fact, there don't seem to be any other options that I can do for ForwardPDF. The dropdown menu for choosing the configuration option seems to be disabled for ForwardPDF for some reason.

---

