---
title: "Open Office constantly crashing"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by L Campbell on 2008-06-19
On my PC with Hardy Heron 8.04, Open Office Writer recently upgraded to version 1:2.4.1.-1ubuntu1.

When I try to copy stuff from this ( [http://www.goldenroadent.net/Lessons/lesson1.htm](http://www.goldenroadent.net/Lessons/lesson1.htm) ) web page, O.O constantly crashes.

Is this a problem other people are having?

Is there a fix for it?

TIA.

---

### Post by forestpixie on 2008-06-19
I had some problems with the oo update when it was in proposed - I had to do a complete removal of all the openoffice packages and reinstall. Then it worked OK for me.

---

### Post by L Campbell on 2008-06-19
> **forestpixie said:**
> I had some problems with the oo update when it was in proposed - I had to do a complete removal of all the openoffice packages and reinstall. Then it worked OK for me.


Thanks for your suggestion.

I believe I can do the removal but I'm not sure how to do the re-install.

If you could give me a pointer in that direction, I would appreciate it.

Kind regards.

---

### Post by forestpixie on 2008-06-19
Do it in synaptic - easy there :)

Search for openoffice.org - mark all the installed packages for complete removal and then use the same search and mark them for installation.

I did try a reinstall but it didn't work for me.

---

### Post by Dedoimedo on 2008-06-19
Hello,
Try uninstalling and purging the package. Then, look for any leftovers of the configuration files in your home directory, manually remove them (backup them up if you want), then reinstall the package.

apt-get remove --purge <package-name>

After that, clean the local repository of downloaded packages:

apt-get autoclean

Then clean the home directory of any leftovers and try a brand new install.

apt-get update
apt-get install <package-name>

Of course, don't forget "sudo".

Dedoimedo

---

### Post by L Campbell on 2008-06-19
> **forestpixie said:**
> Do it in synaptic - easy there :)

Search for openoffice.org - mark all the installed packages for complete removal and then use the same search and mark them for installation.

I did try a reinstall but it didn't work for me.


In Synaptic the 'search' doesn't find 'open office', 'openoffice' or 'openoffice.org'.

I know it is there because I can scroll to it but is the fact that Synaptic search can't find it indicative of a problem?

---

### Post by forestpixie on 2008-06-19
Try hitting the button marked S - so it sorts by installed once you have done a search.

I'd be surprised if they don't get returned in a search - absolutely clueless as to why if that is the case as well

---

### Post by L Campbell on 2008-06-19
> **forestpixie said:**
> Try hitting the button marked S - so it sorts by installed once you have done a search.

I'd be surprised if they don't get returned in a search - absolutely clueless as to why if that is the case as well


OK, that worked perfectly, thanks.

Kind regards.

---

### Post by L Campbell on 2008-06-19
> **forestpixie said:**
> Try hitting the button marked S - so it sorts by installed once you have done a search.

I'd be surprised if they don't get returned in a search - absolutely clueless as to why if that is the case as well

I removed and re-install Open Office and, at first, this didn't help as it still kept crashing.

THEN I found that I had quite a few strange looking files in my Documents folder that were all associated with the link that I included with my initial post.

I strongly suspect that there was some incompatibility between these files and 'OO', so I deleted the files and 'OO' seems to be working correctly again.

BTW, I changed some letters in that link, so that nobody else can get unsuspectingly contaminated by it.

Kind regards.

---

