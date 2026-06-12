---
title: "Scanning Help Needed."
date: 2008-05-29
forum: New to Ubuntu
---

### Post by spotteddog on 2008-05-29
I need help with my scanning/printing. I am completely stumped. I have tried both Xsane and Quiteinsane and things keep getting worse. Using Hardy.

Xsane: the quality is fair, but the colors are all wrong. The colors are in the right range, but they are totally washed out and dull. I have tried changing several of the settings, but I just keep making things worse.

Quiteinsane: the qualify is extremely poor (almost unreadable) and the colors aren't even close. Also, it won't show my printer as an output device, so the only option I have is too save, then print from the saved file.

I'm using an Epson 1660 photo, which the scan apps recognize as an Epson 8300gt. My printer is an iP4500. Scanner works fine in Vista. Printer works fine in both Vista and Hardy.

---

### Post by didac on 2008-05-29
What I do is:

Ctrl-0 to reset gamma , brightness and contrast to default values.

Scan a preview.

Open the Histogram window. Uncheck Intensity, Red, Green. Adjust blue, so that the middle slider will be under the central blue peak. Uncheck blue and check any other colour. Do the same.

After setting intensity and colours with the histogram, I adjust brightness and contrast. 

Or if I'm in a hurry, I do only gamma, brightness, contrast.

My scanner is a HP 38000.

Hope it helps. Maybe you've done it already.

---

### Post by spotteddog on 2008-05-29
> **didac said:**
> What I do is:

Ctrl-0 to reset gamma , brightness and contrast to default values.

Scan a preview.

Open the Histogram window. Uncheck Intensity, Red, Green. Adjust blue, so that the middle slider will be under the central blue peak. Uncheck blue and check any other colour. Do the same.

After setting intensity and colours with the histogram, I adjust brightness and contrast. 

Or if I'm in a hurry, I do only gamma, brightness, contrast.

My scanner is a HP 38000.

Hope it helps. Maybe you've done it already.
I tried what you have suggested and it helps. But the quality isn't anything close to what I can get with Windows apps and drivers. Same printer and scanner in Windows gives me a copy as good as the original. Hardy, at best, gives me a very poor copy.
There are some things I really like about Ubuntu, but after working with Hardy for almost 2 months, I am finding more and more things that can't come close to Windows.

Thank you very much for your help.

---

### Post by P3ngu1n0 on 2008-05-29
just use it with windows, you can move the scanned files from windows to linux is needed

---

### Post by spotteddog on 2008-05-30
> **P3ngu1n0 said:**
> just use it with windows, you can move the scanned files from windows to linux is needed
I have found that if I use Gimp Image Editor, then use some of the "auto" corrections, I can get better quality than just using Xscan or QuiteInsane. Still not perfect though. 
And I can't see rebooting to Vista every time I want to scan/print something. If that's the only option, then there's really not much point even using Ubuntu.

---

