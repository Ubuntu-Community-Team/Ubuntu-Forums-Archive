---
title: "[SOLVED] .pdf that opened two days ago won't open now"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Amanda HazLaPaz on 2008-10-11
I upgraded to 8.04.1 via update manager about a month ago. 

I downloaded a .pdf two days ago that I was able to open immediately after finishing the download (I assume Evince but did not remark upon it). I got about two pages in and then had to abandon it. Computer has since been shut down once.

Tried to open it tonight and could not. Evince froze, Firefox refused to see it. I checked the folder and it had data in it.  Restarted but no joy. Had a friend try to help via IM but he's a Fedora guy and it was a little above my head.

"We" attempted a direct Adobe Reader .deb download, which gave an error message "AdobeReaderxyz could not be opened, because the associated helper application does not exist. Change the association in your preferences."

I checked Add/Remove for some options. I checked Synaptic for "Acroread" per instructions here in the forum and it says I have to have medibuntu repository enabled (I had them under 7.04: did my upgrade do away with it?)

Tried the tar.gz (I know, against the recommendations here in the forum) but I was stumped as to what to do with the result. I'm a year with Ubuntu but still so very much I don't know.

1- WHY won't the .pdf open when it did before?
2- What actions can I take to remedy the situation?

Thanks for all help!

---

### Post by keplerspeed on 2008-10-11
I do not have acroread installed, just evince and KGhostView. Try reinstalling evince, or even try a different pdf viewer, and see if the symptoms persist.

---

### Post by kaibob on 2008-10-11
The easiest way to install Adobe Reader is by way of the Synaptic Package Manager. You do have to have the Medibuntu repository available:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you have Imagemagick installed, you can open the PDF as a check by entering the following in a terminal window:

```
display filename.pdf 
```

If the PDF opens in Adobe Reader or the display utility, then reinstall Evince as previously suggested.

---

### Post by Amanda HazLaPaz on 2008-10-12
keplerspeed and kaibob:

Thanks to you both for your assistance!

I enabled the medibuntu repo because I figured I might need that in the future anyway. I downloaded acroread and associated packages (2) and I was able to open the .pdf in Firefox.

You guys were great help!!

---

### Post by Orange_and_Green on 2008-10-12
The next time you have a .deb you cannot open, try right-clicking->"Open with other application" and select "GDebi Package manager" from the list. If it doesn't appear in the list, try

```
sudo apt-get install gdebi
```

Hope this helps you in the future. The association should be automatically done at install time but apparently a lot of people are missing it...

---

### Post by Amanda HazLaPaz on 2008-10-13
Thanks, Orange-and-Green. Did as you suggested. My only problem now will be *remembering* to do that. Good thing these threads are searchable.

/if I could only recall what it was I was looking for....

---

