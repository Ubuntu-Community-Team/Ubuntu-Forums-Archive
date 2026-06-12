---
title: "Samsung ML-2165 Printer"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by horny-sama on 2014-02-19
I am currently using xubuntu 13.10. I have downloaded the driver from samsung
```
 
cd ./Dekstop/uld
./install

```
Everything went well, so I proceeded with adding it to the printer setting. It works fine. I am able to print multiple pages using Document Viewer, but not adobe reader for some reason. I am just wondering is there a reason behind it? I mean I have been using fedora xfce with adobe reader and it functions 100%

---

### Post by danceswithcats on 2014-07-13
Hi Horny, 

I expect you've got this sorted by now, but, if not, try searching in synaptic for suld-printer-pdf-fix.  You'll need to uninstall the driver and install the chmet repository first, which is a bit of a faff, but the instructions are here: [http://www.bchemnet.com/suldr/suld.html](http://www.bchemnet.com/suldr/suld.html) and I have copied the repository setup section below.

> Setting Up the Repository

    If you performed any installations of the Unified Linux Driver performed using the Samsung installer, these must be completely removed before using the .debs in this repository. See the uninstallation information for your version of the driver.
   
         using a graphical package manager (Synaptic, Ubuntu Software Center, etc.):
            Edit the repository settings (e.g., Synpatic go to Settings -> Repositories) to add:
            deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra
            Or if multi-line input is required:
            URI: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)
            Distribution: debian
            Section: extra
    IMPORTANT: The distribution and section must be entered exactly as above. Do not substitute the name of your own distribution, translate the words, or use a default section - it won't work. I get hundreds of errors on the server each day from people who replace one or more of the terms above (especially Ubuntu users using the code name of their particular release).

    Install the GPG key (last update: 18 Oct 2009) for the repository (if you skip this step, you will get warnings about installing unauthenticated packages), using one of the following methods.
        In a terminal, as root, enter the command (the - marks are important):
        wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | apt-key add -
       [B] Or if you are using sudo:
        sudo wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -[/B]
        Download the key file and add it to your graphical package manager list of keys.
        Download the key file and execute the following (as root) in a terminal, in the folder with the key file:
        apt-key add suldr.gpg
       [B] Or if you are using sudo:
        sudo apt-key add suldr.gpg[/B]
   ** Refresh your repository listings:**
        On a terminal (as root):
        apt-get update
    Or if using sudo:
        sudo apt-get update
      [B]  Or in a graphical manager, click the reload or refresh button.
        The suld-* packages should now appear in your list of available packages to install.[/B]

I've bolded the bits I used, since they were successful for me.

The excellent, but slightly complicated page of the most revered maintainer of Samsung drivers for Linux, from which I copied these instructions, is here: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

Best of luck,

DWC



UPDATE I've just found a much clearer set of instructions from the magnificently hairdo-ed Zeth: Ignore the above and do use this page: [http://zeth.net/2013/01/14/samsung_printers_on_ubuntu.html](http://zeth.net/2013/01/14/samsung_printers_on_ubuntu.html)

---

