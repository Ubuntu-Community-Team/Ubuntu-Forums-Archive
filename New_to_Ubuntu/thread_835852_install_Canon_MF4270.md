---
title: "install Canon MF4270"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by fredfelter on 2008-06-20
There is an archived thread on this subject that ended in May but I can't make the info work for me.
Ubuntu 8.04 on Thinkpad T22

I believe I've downloaded the proper apps, GhostScript and the Canon driver ver. 1.05. 
One poster said all he had to do was dbl. click on the Debian files contained in the download and it installed. When I do that it asks if I want to Run it but when I do nothing seems to occur.

Here is what is happening to me: Printing > New Printer > searching > it finds my Canon complete with proper IP address > searching for drivers > up comes a screen asking to select a printer from a list which then directs me to a generic driver that doesn't work OR it directs me to Provide PPD file. There actually is such a file within one of the driver download packages but using that doesn't work. It looks like I need to use the Debian files but I can't see how to make the printer config app see them.

Thanks for any help in advance.

---

### Post by phidia on 2008-06-20
Your printer is listed at the openprinting database and they claim it works "perfectly". Go to the page [here]("http://openprinting.org/show_printer.cgi?recnum=Canon-MF4270") for the printer listing. The driver for the MF4270 which seems to be the same as the 4150 is found [here]("http://support-au.canon.com.au/EN/search?canonsearch=1&lang=EN&category=All-in-One+Printers&series=Laser+Multifunction&model=Laser+imageCLASS+MF4140%2fMF4150&menu=Download").

---

### Post by fredfelter on 2008-06-20
Thanks phidia but as you'll see in my posting I've already downloaded the Canon driver. The problem I'm having is how to get the printer config app to recognize the driver.

---

### Post by phidia on 2008-06-20
> **fredfelter said:**
> Thanks phidia but as you'll see in my posting I've already downloaded the Canon driver. The problem I'm having is how to get the printer config app to recognize the driver.

The driver from that link is a later version and you will have to select the provide PPD file. Are you selecting the printer as a LPD/LPR Host?

---

### Post by fredfelter on 2008-06-21
Thanks for hanging in there with me Phidia.

No I'm not selecting LPD/LPR because I already see the Canon listed as a choice and, besides, LPD/LPR leads me to the same generic driver/PPD screen anyway.

Here's what's happening: Printing > Printer config > New Printer > the Canon is listed with its IP address and Port > Forward > searching for drivers > the generic driver or provide PPD file screen > select PPD > browse to the 2 source files in the driver download (no PPD in the "cups commom" but there is a PPD in the "cups lb") > open the "cups lb > PPD > 4200 ZS.ppd > back to New Printer > rename > apply > adding > now I see the Canon listed in Printer Config-local host as the default printer but the print test page is greyed out and the printer doesn't work.

It seems like I'm close to making this happen but I don't know what else to try.

---

### Post by darthbrader on 2008-06-21
I've also been trying to get the MF4200 working in 8.04 Hardy.  I downloaded the australian drivers linked from the [openprinting]("http://openprinting.org/show_printer.cgi?recnum=Canon-MF4270") page.  My printer config shows:
Device URI:  socket://1.2.3.4:9100 (where 1.2.3.4 is the printer's IP)
Make and Model: Canon MF4200 Series UFRII LT Ver.1.7

I selected the PPD file installed by the .deb package from Canon here:
/usr/share/cups/model/CNCUPSMF4200ZK.ppd

I had to fiddle around with it a bit and reboot the printer, but it seems to have just started working.  I've generally found this printer's networking to be a bit flaky... it was a bunch of shenanigans to get it working with Macs as well.

---

### Post by fredfelter on 2008-06-21
Thanks for the reply Darthbrader.
I just changed the PPD file to the ZK one from the ZS one I was previously using but that made no difference.
Can you do a "print test page"? I can't because it is greyed out, suggesting I don't have the printer configured correctly.

---

### Post by darthbrader on 2008-06-21
Yeah, it seems to be working OK.  The printer status shows idle, and I can print the test page.  Are you using socket://... for the URI instead of lpd://..., as indicated on the openprinting page for the MF4270?  

You also said your driver version was 1.05; I'm using 1.7.  The only difference between the 'S' and the 'K' should be that 'S' is for the United States driver while the 'K' is for the United Kingdom driver.  The openprinting page implies that the US driver isn't available, though obviously you found one.  I'm not sure what that's all about, but I'd guess the driver version is more important than the country designation.  

Good luck!

---

### Post by fredfelter on 2008-06-21
What I have in "Printer configuration-localhost" is:
   
Device URI socket://xxx.xxx.x.xx:9100 (x's being the IP address of printer according to the settings I got from the printer itself)
   Description: blank
   Location: fred-laptop
   Make and model: Canon MF4200 Series UFR11 LT ver. 1.7  
   Printer status: stopped
   Default printer: this is ...
   Tests and maintenance: 3 buttons all greyed out

It sure looks like it is ready to go except for the test buttons.

---

### Post by fredfelter on 2008-06-21
An associated question:

Is there another download to do in addition to the .ppd file? I was reviewing the CUPS page and noted that they speak of a driver download plus a PPD download. I have done the .ppd one but is there more because you mention the Debian package and in order to get the .ppd files I did not have to open any Debian folders?

Thanks

---

### Post by darthbrader on 2008-06-21
Perhaps... the file I got from Canon was called UFR_II_Printer_Driver_for_Linux_Driver_v170_uk_EN.tar.gz.  It contained two debian packages under 32-bit_driver/debian.  They are called cndrvcups-common_1.70-1_i386.deb and cndrvcups-ufr2-uk_1.70-1_i386.deb.  They installed a bunch of ppd files, and presumably some other stuff as well.  Perhaps that's what you're missing?

Good luck!

---

### Post by phidia on 2008-06-22
Yeah that link I posted before had the latest driver 1.07 I think?
Try that.

---

### Post by cyberkost on 2008-12-27
Gents,

has anyone installed MF4270 completely -- such that both scanning AND printing works.  What about the issue of only flipping the pages on the short side in duplex printing?  Has it been overcome?

More generally, would you recommend Canon MF4270 over Brother MFC-7840W (wireless networking, better Linux support, but no duplex and more expensive printing)?

---

### Post by alexcuervo on 2009-04-24
For 64bit users there is a good guide here
For the printer part
[http://queleimporta.com/installing-canon-imageclass-mf4270-on-ubuntu-64-bit/]("http://queleimporta.com/installing-canon-imageclass-mf4270-on-ubuntu-64-bit/")

For the scanner part:
[http://queleimporta.com/installing-canons-imageclass-mf4270-scanner-on-ubuntu-64-bit/]("http://queleimporta.com/installing-canons-imageclass-mf4270-scanner-on-ubuntu-64-bit/")

---

### Post by Francewhoa on 2009-05-23
Click here for [*HOWTO: Install Canon ImageCLASS MF4270 Multifunction driver.*]("http://ubuntuforums.org/showthread.php?t=1140724")

---

