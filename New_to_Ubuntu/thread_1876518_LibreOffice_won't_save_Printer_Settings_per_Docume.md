---
title: "LibreOffice won't save Printer Settings per Document."
date: 2011-11-06
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-11-06
I hope this does not count as cross-posting, because I have already tried, without success, to get help on OOo Forum ([http://user.services.openoffice.org/en/forum/viewtopic.php?f=101&t=43438](http://user.services.openoffice.org/en/forum/viewtopic.php?f=101&t=43438)) and via LibreOffice Users Mailing List ([http://nabble.documentfoundation.org/LibreOffice-Won-t-Remember-Printer-Settings-td3480528.html](http://nabble.documentfoundation.org/LibreOffice-Won-t-Remember-Printer-Settings-td3480528.html)).
My last hope is that somebody on Ubuntu Forum may be able to cast some light...

I have had OpenOffice in Ubuntu for some years, and saving Printer Settings works just fine.
My understanding of how it works is as follows (please correct if wrong):

A. I can set overall System-wide default printer settings via: Ubuntu > System > Administration > Printing > Printer > Properties > Printer Options.
B. I can set Document-specific printer settings via: OpenOffice > File > Printer Settings > Properties.
C. I can set printer settings for the next Print only via: OpenOffice > File > Print > Properties.

So what gets printed is whatever I set at A, unless I over-ride it for that Document at B, or for that particular Print at C.
If I make a change at A, it then appears at B & C.
If I make a change at B, it then appears at C.

Perfect!

With Ubuntu 11.04, OpenOffice was replaced by LibreOffice and something in the above is broken, at least for me:
What I set at A appears at B & C, prints as required, and stays until deliberately changed again - OK.
What I set at C prints as required (one time) then resets to default as A - OK.
But - Nothing I set at B has any effect at all on C, nor on what is printed!
This means I cannot set any Printer Settings to stick with a Document, but have to either set them as system-wide defaults at A, or reset them every Print at C.

Unacceptable!

So I would appreciate any suggestions for diagnosing & fixing my problem!

Is this feature working OK for others in 11.04?

Thanks!

---

### Post by CryptoPaul on 2011-11-06
Noticed the same thing.

Using LibreOffice 3.4.3 (Build:302) / KDE Platform Version 4.7.2 / Kubuntu 11.10

( "Tools &#8594; Options &#8594; Load/Save &#8594; General &#8594; Load printer settings with the document" option is selected )

Printer settings appear to be no longer saved (or loaded?) with the document.

---

