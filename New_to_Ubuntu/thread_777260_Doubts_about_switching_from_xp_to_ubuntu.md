---
title: "Doubts about switching from xp to ubuntu"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by hypertonic on 2008-05-01
Hi,

I recently tried ubuntu 8.04LTS, and I fell in love.
The problem is, I'm in college studying civil engineering, and I need quite the bit of scientific applications and features (for example, I really need trendlines in my excel, which isn't a feature in openoffice.org, or I really need something as winedt, or matlab, maple,...)
Now, I know I could run most of those programs using Wine, but I use them so often, that I don't want the hassle around it.

You could say, install them both, but my internal harddrive is only 60Gigs large, which isn't much to run 2 OS's and store all my data.

So, my question is, is there any way I could modify my ubuntu/is there a list of linux-based scientific programs with their windows equivalent, so that I could switch over to linux, and lose none of my functionality?

regards,
hypertonic

---

### Post by Monicker on 2008-05-01
I'm not familiar enough with matlab and such to know if they have a linux counterpart.

If there are no linux equivalents to apps which you must have for your studies, then I would use virtualbox or vmware player to use a minimal install of Windows just for those applications.

---

### Post by mrdosa on 2008-05-01
I am using a dual boot system with xp and Ubuntu on a 40GB hDD!!! And they are working like they should!!:)

---

### Post by Cadmus on 2008-05-01
Take a look at [osalt]("http://www.osalt.com/") and see if any of your programs are given equivalents, then have a look and see if they offer the functionality you need.

---

### Post by philliptweedie on 2008-05-01
I wasn't too sure what MATLAB was so I googled it and it says that it is compatible with linux :

[http://www.mathworks.com/products/matlab/requirements.html](http://www.mathworks.com/products/matlab/requirements.html)

Also winedt if it's this [http://www.winedt.com/](http://www.winedt.com/) looks like it would have lots of equivalents. Maybe even Gedit would do the trick.

Also maple says it supports linux as well :

[http://www.maplesoft.com/products/Maple11/system_requirements.aspx](http://www.maplesoft.com/products/Maple11/system_requirements.aspx)

---

### Post by aeiah on 2008-05-01
maple and matlab are available for linux. winedt is an editor, no? you could try emacs, vim etc. i guess it depends what features of winedt you like (ive never used it myself)

---

### Post by Helios1276 on 2008-05-01
> **mahender.mandala said:**
> I am using a dual boot system with xp and Ubuntu on a 40GB hDD!!! And they are working like they should!!:)

I have to agree, Ubuntu would be alright with say 15gb. So you can do your work ,with programs your comfortable with, in xp and have all the fun of Ubuntu for surfing,no viruses,open source, posting problems to the forums;)...essentialy theres your cake and your allowed to eat it as well

---

### Post by regomodo on 2008-05-01
open office can do trendlines but Gnumeric is a lot better than it and Excel.

Octave is similar to Matlab

---

### Post by Nepherte on 2008-05-01
I'm studying for engineer myself and I can tell you I can tell you that there are linux versions for both Matlab and Maple. For winedt there are enough fully equivalent linux programs.

---

### Post by movrshakr on 2008-05-01
Here is a site that shows linux substitutes for Windows programs...

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)


I saw another one recently that I think was a .ru site, and it was even more complete than the above.  Unfortunately, if I bookmarked it, and I should have, I can't find where I put it.  Darn.

AH, found it...

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html")

---

### Post by cartisdm on 2008-05-01
I'm running Ubuntu on the 15gb partition of my 120 and XP on the other (only on accident because I wasn't paying attention when I installed it).  But it's plenty for me and I use ubuntu 98% of the time.  Anytime I need sometime extra large to be stored I just mount my windows partition and save to it, works like a charm.

Soon as school is over (two more days!) I'll reinstall everything but for now I just need to have stuff readily available for projects etc.

Keep in mind though, even with linux equivalents it can be difficult to do a homework assignment, trust me.  Teachers set up projects (and their directions) to be program specific.  The chances are you don't know completely what you're doing (since that's why it's being taught in the first place) and it's can be more work for you to do it on something else.  I've had lots of excel assignments working with data analysis in management plugins that is just too hard to figure out in OOo

---

### Post by hypertonic on 2008-05-01
thank you all for the answers. I think I'll make it a dual boot for now, just until my team-assignment is finished, because the other two in my team don't know linux. After that, I'm switching.

regards,
hype

---

### Post by Stefanie on 2008-05-01
if you use winedt for latex, you can try kile. it's built for KDE but it runs without any problems on my ubuntu install, and it's really the best latex editor i've ever seen :-)

---

### Post by Cadmus on 2008-05-01
> **hypertonic said:**
> thank you all for the answers. I think I'll make it a dual boot for now, just until my team-assignment is finished, because the other two in my team don't know linux. After that, I'm switching.

regards,
hype

Good call, FLOSS and such are all well and good, but there's a lot to be said for just sticking where you are until it's not critical.

---

### Post by Myglaren on 2008-05-01
Damnit, post disappeared.

How about installing a larger capacity drive and dual booting, or dual booting anyway and shift your data to an external drive?

---

### Post by gunksta on 2008-05-01
I'll be the one voice of caution in all of this. Previous posters are right that many scientific programs are now available for linux. For example, the newest version of SPSS is written in Java and can be obtained for Linux, Mac OS X and Windows.

But, you also mentioned Excel. OpenOffice.org (OOo) is many things, most of them wonderful. I have found in my own personal work, where compatibility is less of a concern, that OOo works perfectly. There are a few features missing, but you can look at:

[http://extensions.services.openoffice.org/](http://extensions.services.openoffice.org/)

You may be able to find an extension that does what you want. 

(Before I say this, I shall don my flame proof suit.) WARNING: OOo is not 100% compatible with MS Office. There, I said it. It has nearly all the same features but its ability to export to the binary MS file ain't perfect. In this case I'm talking about using OOo Calc saving a file as a .xls rather than a .ods. For example (YMMV), I use Pivot Tables nearly every day. OOo has a similar feature called the Data Pilot that can give you pretty much the same functionality, once you get used to the minor differences in form function and terminology. But, if I use OOo Calc to open up a .xls file with a Pivot Table, I can't edit the Pivot Table, and some really strange things happen if I save a Data Pilot to a .xls and open it in Excel 2003. If you need to be able to exchange information with MS Office users AND you need Pivot Tables, OOo Calc is of limited use to you.

Similar problems arise in saving Word documents (.doc). If you insert a chart (OLE Extension) into a .doc file and open the file with Word 2003, you can see the resulting chart just fine, but Word doesn't know how to open it up and let you edit the data or change the settings of the chart. You get an error, telling you it doesn't understand this call for OOo Calc. 

Again, YMMV. The functionality _is_ there, but the file fidelity is problematic. If you are going to submit printed papers, then OOo really has you covered 99% of the time and doesn't have some of MS Office's problems such as problems with regression calculation with very small and very large numbers.

Depending on what you are doing, these may or may not be trivial problems. And, depending on the size of the data sets you are working with and the amount of RAM in your system, emulation such as Virtual Box, etc. may or may not be the solution. I don't know. Like I said, YMMV.

I really do hope I don't get flamed here. I am not trying to spread FUD or anything like that. I have offered specific examples, based on my own professional experience where compatibility between OOo and MS Office are problematic. In all cases, OOo has the capacity and works perfectly when I save to the native file formats, or exchange files with other OOo users. But, exchanging files with MS Office users is still a challenge.

Recommendations: I agree with your assessment. Stay where you are for right now. If your hard drive is large enough, I would maintain the ability to dual boot. This way you can use ALL of the software you may need to use. Ubuntu can now read and write to NTFS drives, so sharing information between the two systems has gotten much easier.

---

### Post by Gripp on 2008-05-01
> **movrshakr said:**
> Here is a site that shows linux substitutes for Windows programs...

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)


I saw another one recently that I think was a .ru site, and it was even more complete than the above.  Unfortunately, if I bookmarked it, and I should have, I can't find where I put it.  Darn.

AH, found it...

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html")

damnit, you beat me to it!

yeah, [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) has a great list of EQ's and there are replacements for mathlab and maple and whatnot. 

as for trend lines... not sure how to help you there.  there are programs like LabPlot that may perform what you;re looking for there

what i would do if i were you is get Adept installed, which you can do from the add/remove window

then fire up adept by using the command line "sudo adept_manager"

it has a much broader range of software to choose from, and some nice search features too.  

good luck!

---

### Post by Kinst on 2008-05-01
Uh maple is native for linux. I have maple.

Also I have excel using wine cause I don't particularly like openoffice.

---

### Post by forumache on 2008-05-03
You can also try running Windows inside a VirtualBox under Linux.

---

