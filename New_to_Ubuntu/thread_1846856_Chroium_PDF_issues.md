---
title: "Chroium PDF issues"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by Syndacate on 2011-09-19
Hey,

Does anybody have issues with Chromium not displaying embedded PDFs?

I copied the libpdf.so from the standard chrome install into the /usr/lib/chromium-browser AND the /usr/lib64/chromium-browser directories (at separate times), and checked that it was enabled in the about:plugins page in chromium, it's there, but there's no MIME type associated with it (is that a problem?) - there's none in regular chrome's plugin list, either.  Though the plugin IS enabled there.

I've also tried making a symlink to the chrome dir, no luck there.

Anybody have any suggestions?  I'd really like to use chromium..it has some weird things that chrome does or doesn't do (small things).  Firefox just doesn't do it for me for some reason, feels bulky.

Any tips?

EDIT:
Before I installed the plugin it just downloaded PDFs, after I just get the gray screen that says "Missing Plugin."

---

### Post by Sergio.G on 2011-09-19
Hi,

do you have the enable-plugins in the Application launcher options?
give a right click on the chromium application launcher, check in the command field if this is written:

/usr/bin/chromium-browser --enable-plugins %U

As well you might want to check the libpdf.so file permission, should be 755

Cheers.
Hope it helps.

---

### Post by Syndacate on 2011-09-19
> **Sergio.G said:**
> Hi,

do you have the enable-plugins in the Application launcher options?
give a right click on the chromium application launcher, check in the command field if this is written:

/usr/bin/chromium-browser --enable-plugins %U

As well you might want to check the libpdf.so file permission, should be 755

Cheers.
Hope it helps.

I didn't have the enable-plugins option nor the correct permission on the object, but neither made a difference.

It didn't have execution permission for other, which I thought was weird, but then again neither does the standard chrome plugin in /opt/google/chrome/libpdf.so, which has its permissions set to 644.

But yeah, tried launching chromium by doing:
chromium-browser --enable-plugins from the terminal, that didn't do anything, nor did adding the option to the launcher, which is in essence the same thing.

Blah, I had high hopes after fixing both of those, but apparently no difference :'(.

This problem is killing me, and the only info I can find about it is from like '09.

EDIT:
To clarify about the info from '09 those typically just say link or copy the libpdf.so from chrome to the /usr/lib/chromium-browser/ dir.

---

### Post by Sergio.G on 2011-09-19
Hi, 

Well apparently you are not the only one having this issue, made a search around and found that it is a common problem.

Thing is that in June this year I did this procedure ([http://www.omgubuntu.co.uk/2010/07/use-google-chrome%E2%80%99s-native-pdf-reader-in-chromium/]("http://www.omgubuntu.co.uk/2010/07/use-google-chrome%E2%80%99s-native-pdf-reader-in-chromium/")) in my 64 bit Ubuntu (Lucid) installation and it worked and still does. 

Today I did it again and it failed with the latest Chrome dev installation

Checking the libpdf.so from the Chrome dev I downloaded back then, the file size is 15 MB and the one I downloaded today is only 5.7 MB

Cheers.

---

### Post by Syndacate on 2011-09-25
> **Sergio.G said:**
> Hi, 

Well apparently you are not the only one having this issue, made a search around and found that it is a common problem.

Thing is that in June this year I did this procedure ([http://www.omgubuntu.co.uk/2010/07/use-google-chrome%E2%80%99s-native-pdf-reader-in-chromium/]("http://www.omgubuntu.co.uk/2010/07/use-google-chrome%E2%80%99s-native-pdf-reader-in-chromium/")) in my 64 bit Ubuntu (Lucid) installation and it worked and still does. 

Today I did it again and it failed with the latest Chrome dev installation

Checking the libpdf.so from the Chrome dev I downloaded back then, the file size is 15 MB and the one I downloaded today is only 5.7 MB

Cheers.

Yeah, seems it's not an uncommon problem, but linking or copying the object file seems to do the trick for everybody.

For me, I linked it, it WAS working, then chrome fu8king updated and it stopped :(.  I tried both re-linking (although that shouldn't make a difference) and re-copying, both failed.

---

### Post by Syndacate on 2011-09-25
This just keeps getting weirder and weirder.

Before the permissions were set to 755, I set them to 000 then set them to 777, disabled the plugin through about:plugins, then restarted chromium.

Now it's at a state where every other (exactly every other) PDF works.  First time I click a PDF, it opens in chromium, second time I click it, it opens it in document viewer, third time I click it, it opens in chromium, etc.

The hell?

Is the PDF plugin supposed to be enable or disabled?  Things say it should be enabled a lot, but those keep yielding the missing plugin gray screen error while right now it being disabled is working exactly 50% of the time.  Anybody have any suggestions??  I'm thinking possibly conflicting PDF plugins or something??

---

