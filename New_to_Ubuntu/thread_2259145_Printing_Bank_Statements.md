---
title: "Printing Bank Statements"
date: 2015-01-02
forum: New to Ubuntu
---

### Post by MalcolmS on 2015-01-02
I am using Ubuntu 14.10 for personal and business purposes. My problem is that when connected to the Royal Bank of Scotland website I can only print one page** of** a set of transaction pages. This is in direct contrast to working through Microsoft windows. Royal Bank have no plans to support Ubuntu/Linux users. I think the problem can be easily fixed as it is probably a simple print function which has been overlooked? Anyone offer any constrcutive steps?

---

### Post by pfeiffep on 2015-01-02
Hi MalcolmS, welcome to the forum. 
My experience certainly is different from yours as I'm in the US, and run 14.04. I use Mint as well as on line banking. I use FireFox.[INDENT]My bank offers the option to download as pdf 
Mint offers the option to export all as cvs
[/INDENT]
 If you can view all the transactions just by scrolling you might consider saving the web page as "web page complete"

---

### Post by whitesmith on 2015-01-02
Try using a native PDF reader/printer (e.g., Evince with Gnome or LibreOffice otherwise). Adobe's stuff for Linux hasn't been working in months. Cheers!

---

### Post by buzzingrobot on 2015-01-02
If the bank offers the option to download the statement, as a PDF or in another format, do that and then try printing that file.

Also, if you install the "cups-pdf" package,  Firefox will add the option to print to PDF to its File->Print dialogue.

---

### Post by MalcolmS on 2015-01-03
Hi Pete, 

Thanks for suggestion.
My 'feeling' is that the problem is a print control issue on Ubuntu and Linux/mint. I use both and Firefox. However, as you say I can try saving pdf of the transaction list on the screen and then address it using evince (I can't find evince at the moment!). Basically, when printing the data it prints one page regardless of whether statements or a historical list of transactions. I will investigate further and thank you for your suggestions. Unfortunately, I am not very proficient with these issues but I will persevere to get more acquainted.
malcolm.

---

### Post by Paulgirardin on 2015-01-03
Document Viewer in Ubuntu is Evince.

---

### Post by JeQhdMD on 2015-01-03
Don't think main cause(s) re printing is the OS . . but more browser related (javascript, html4/5 etc.).    Suggest to try another browser such as Chrome or Chromium.   IF you printer(s) have wireless, you can enable them for cloud print via Google technology (need to get IP address of the printer and register it via Google).   That way, you can print to your heart's content, irrespective of OS.

---

### Post by MalcolmS on 2015-01-03
Hi Pete,

What printers are you using and which driver? I am using HP 1020 (wired connection) and HP 3055A (wireless). I had difficulty with HP1020 (probably because it is quite old) and had to seek a driver which is Hplip. This arose because with paper run out on the HP1020 it would cease to print.

Thanks,
Malcolm.

---

### Post by pfeiffep on 2015-01-03
Hi MalcolmS,

I'm using a HP c6200 series (photo smart all in one) connected to desktop bu usb, connected to laptop through wireless router.  The drivers were selected by Ubuntu 14.04.

---

### Post by oldfred on 2015-01-04
Do they support downloaded transactions? 
Banks in USA normally do.

My current bank offers cvs, and only Quicken qfx where my old bank also had OFX. But it turns out I can downlod QFX and import those into my kmymoney as if it was OFX. I have then use the kymoney save as sqlite files and can run sql queries and create my own reports in HTML. Kmymoney has reports but I wanted to learn python, sql, & reporting.

---

### Post by mastablasta on 2015-01-05
> **MalcolmS said:**
> I am using Ubuntu 14.10 for personal and business purposes. My problem is that when connected to the Royal Bank of Scotland website I can only print one page** of** a set of transaction pages. This is in direct contrast to working through Microsoft windows. Royal Bank have no plans to support Ubuntu/Linux users. I think the problem can be easily fixed as it is probably a simple print function which has been overlooked? Anyone offer any constrcutive steps?

they would need to know how these are displayed. someone using ubuntu and your bank would be best to help. As long as the statements are in browser they should be printed as they are on screen. it is hard to say what your browser settings are. as other suggested you could try saving them to a file and print then. you can also try different browser. My consumer account is web based and since it is web based it is basically system agnostic. i can use it the same in Windows as well as in Linux or Andorid. you say you can print only one page. if you go to print preview - how many pages is it showing?

sadly my bank business account uses another interrface and USB chip that both work only on Windows :(. on the plus side it is super easy to make end of year reports.

> **oldfred said:**
>  Kmymoney has reports but I wanted to learn python, sql, & reporting.

:lolflag:

---

