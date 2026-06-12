---
title: "Create and Display Thumbnails for VCF files in Nautilus"
date: 2017-01-26
forum: Programming Talk
---

### Post by largewebsite on 2017-01-26
Would like to develop a script or a program, or to have someone help develop a script that allows nautilus or another file  browser in Ubuntu to create thumbnails for a folder of single vcf files into images of business cards -  showing the email, the name, the phone, the address, the company name  the title and the photograph of each vcf file in Nautilus or another  file browser. 

microsoft outlook seemed to be the only product that allowed for contacts to be displayed as business cards with a photo and all the information layed out on the screen and you could select the number of columns by zooming out and more photos would be shown. by clicking on it or right clicking you could edit them, email them call them, etc... you could also edit the display by specifying that you want the picture to be shown or not shown and to choose to display the name only or to select the fields you wanted to see on the card thus making the card bigger or smaller on the display based on the information in it.


[https://scontent.fewr1-2.fna.fbcdn.net/v/t1.0-9/16114961_716440895186862_5227249748106854816_n.jpg?oh=676cf69b2d80ef09674c781f4e650f99&oe=5910889A](https://scontent.fewr1-2.fna.fbcdn.net/v/t1.0-9/16114961_716440895186862_5227249748106854816_n.jpg?oh=676cf69b2d80ef09674c781f4e650f99&oe=5910889A)
This  is the original view in Microsoft Outlook - you can change zoom and you  could see more contacts and more columns on the same page - shows the  photo and all the information

[https://scontent.fewr1-2.fna.fbcdn.net/v/t31.0-8/16300471_716440801853538_2432718145022217327_o.jpg?oh=d8343271cee359bcab35bc1a2e820501&oe=594980A2](https://scontent.fewr1-2.fna.fbcdn.net/v/t31.0-8/16300471_716440801853538_2432718145022217327_o.jpg?oh=d8343271cee359bcab35bc1a2e820501&oe=594980A2)
This  is a view created in nautilus how vcf files can be displayed as  business card view in nautilus or another file browser in Ubuntu. Would  be great to see the VCF files as contacts - and to be able to edit them  right here and eventually develop some way to call or email, skype them,  open their facebook page or other web sites right from here. and to change the way these thumbnails are created and displayed.


Also would be good to develop a similar type of a solution  in thunderbird where you can have a business card view the same way you  would have in outlook. (

- being able to display the vcf cards in  ubuntu file browsers as images of the cards (thumbnails), 
- the ability to click on  them and to select which fields are being shown in the thumbnail (or more likely a script to change all the thumbnails in a folder and you can select how the thumbnails are to be created and which field are to be displays,
- the ability to edit  these cards through a nice interface, although this is not nessesary at first as these are just text files and can be edited with an editor
- the ability to show the business  card view in Thunderbird and to be able to set the number of columns and  the size of the cards to display the same way you can do it in  Microsoft Outlook. (this is another task that can be done in Thunderbird just to have another way to view these cards if you wanted to see them in the same business card view in Thunderbird that already does many of the other functions

This ability to see a list of a grid of 30+ cards on  each page and to scroll down by page is extremely useful and I would  like to contribute to developing this as a free solution for others.

have been through most scripts and ubuntu information  and didnt  find anything useful yet - there are a couple of scripts one can start  with that allow you to work with VCF files in Linux and that allow you to create thumbnails.

 There are also a  few useful free programs in windows that should be created in linux as  well if they dont exist 

- split a multi vcf file into single vcf files,  
- unite multiple single vcf files or multi vcf files into one large multi  vcf file, 
- the ability to create thumbnails for all vcf  files in a folder that would look like the images above (while allowing you to select which fields to display and which to omit (no web site shown on the thumbnails for example, or no picture shown to make the business cards smaller (you could just rerun the script to change the displayed thumbnails in the folder
- small  business cards with the photo, the name, company name, title, email,  phone number, web site etc and maybe the ability which fields to display  and which not to display. 
- ability to edit a vcf file in a nice form  fields would be nice but is the last thing to do as you can just edit  them as text, 
- the ability to drop a photo onto a vcf card file in  nautilus for that vcf file to accept that photo as the new photo for the  vcf file, or as a second photo if that is possible in vcf files (we already have a written script that allows an image file to  be dropped onto a contact in thunderbird and that contact automatically  changes to consider the new image as the photo for that contact, and we can post that script here, maybe  we can rewrite it to be useful in a file browser such as nautilus or  another file browser, 
- maybe a way to right click a vcf file and call  it through skype, open its web site in the browser or email it using  thunderbird. 

all of this can be done in a seperate program but its just  as easy and probably more useful to do this in nautilus or  another file manager, and can be  used on the phone eventually as just using folders of images - that you  can see combine open up and just store in seperate folders is extremely  useful. 

You can use existing programs to compare folders between the  phone and the computer or between contacts downloaded from gmail,  iphone, android blackberry thunderbird outlook etc all as just comparing  folders with vcf files to one another.:popcorn:

---

### Post by wildmanne39 on 2017-01-26
*Thread moved to **{forum for better support}**.*

Please use thumbnails or url's when posting images because many people have slow or limited connections.

---

### Post by largewebsite on 2017-01-26
thank you. will do

[https://launchpad.net/%7Eatareao/+archive/ubuntu/thumbnailers](https://launchpad.net/%7Eatareao/+archive/ubuntu/thumbnailers)

Thumbnailer for Ubuntu

[https://github.com/jeroendesloovere/vcard](https://github.com/jeroendesloovere/vcard)

[https://sourceforge.net/projects/csv2vcard/](https://sourceforge.net/projects/csv2vcard/) - a program allowing to convert CSV comma seperated list of contacts into vcards

This is a list of various Linux VCard programs that we might be able to use to implement as part of the overall scrips or as a separate piece of software

[http://tuxmobil.org/vcard.html](http://tuxmobil.org/vcard.html)

[h=1]Linux and vCards[/h]  Vcard is the industry standard    [RFC]("http://rfc.net/") [ ]("http://tuxmobil.org/links.html")    2426 for managing contact information and can be imported by most mailers or PIM software. They are an existing and widely-used standard for personal user information storage, somewhat like a business card. 


[h=2]Conversion Tools[/h] [h=3]PHP vCard Creator[/h]     [PHP vCard Creator]("http://www.stab.nu/vcard/") [ ]("http://tuxmobil.org/links.html")  is a PHP function for creating vCard files conforming to the vCard 3.0 specification. 

 [h=3]csv2vcard[/h]     [Csv2vcard]("http://csv2vcard.sourceforge.net/") [ [IMG]http://tuxmobil.org/pics/extlink.png[/IMG] ]("http://tuxmobil.org/links.html")  is a program for converting CSV (comma separated values, as exported by software such as MS Outlook) files containing contact information to the industry standard vcard format, which can be imported by most mailers and PIM software (optimized for Evolution). It's based on a Perl script by Michael MacDonald of Ximian. Csv2vcard can be used to convert any CSV format, not just the English Outlook output. 
 [h=3]LDIF to VCARD conversion script[/h]     [LDIF to VCARD conversion script]("http://www.barninger.com/ldif_to_vcard/") [ [IMG]http://tuxmobil.org/pics/extlink.png[/IMG] ]("http://tuxmobil.org/links.html")  converts an LDIF address book file, such as that exported from Netscape, to VCARD format for use with programs such as GnomeCard. 
 [h=3]2vcard[/h]     [2vcard]("http://www.netmeister.org/apps/2vcard/index.html") is a Perl script to convert an addressbook to the popular VCARD file format. Currently, it can convert mutt's alias as well as pine's addressbook format. 

 [h=3]PHP vCard[/h]     [PHP vCard]("http://www.bitfolge.de/phpvcard")     generates vCards from any data. This is useful if you have a lot contact information stored in regular databases and want to make them available to end users as comfortable as possible. vCard files are supported by many PIMs. 

 [h=3]ma2p[/h]     [ma2p]("http://web.archive.org/web/*/http://icewall.glavnet.ru/ma2p") [ ]("http://tuxmobil.org/archived.html") is a converter from Mozilla Address Book to Palm Pilot and Mobile Phone (vCard format). 

 [h=3]Handy[/h]     [Handy]("http://www.theossoft.net/handy.html")   is a small console program to convert the output of Lotus Notes client  version 5.x into a vCal Version 2.0 file and/or sends the appointments  to a cellphone of type SIEMENS S45 and maybe S35 also. 

 [h=2]Miscellaneous Applications[/h] [h=3]vCard[/h]     [vCard]("http://www.flaimo.com/scripts.php") [ ]("http://tuxmobil.org/links.html") generates VCF files for importing personal data into vCard-compatible programs. 

 [h=3]vCard4J[/h]     [vCard4J]("http://sourceforge.net/projects/vcard4j/") [ ]("http://tuxmobil.org/links.html")  is a complete toolkit to manipulate vCards (RFC 2426) in Java. It contains a parser to read vCard files. It also includes a compiler to extend the library. vCard types are defined in a XML file, making it easy to add custom types. It also contains XSLTs to convert the internal DOM structure into vCards 3.0, xHTML, or other formats. 

 [h=2]Apps for Mobile Phones[/h] [h=3]SCMxx[/h]     [SCMxx]("http://www.hendrik-sattler.de/scmxx/") [ ]("http://tuxmobil.org/links.html") allows you to exchange certain types of data with mobile phones made by Siemens. Some of the data that can be exchanged include logos, ring tones, vCalendars, phonebook entries, and SMS messages. It was created to work with an S35i but other models can be supported. SCMxx uses the AT command set published by Siemens to do its work. 

 [h=3]sambru[/h]     [SamBru (Samsung Backup and Restore Utility)]("http://lager.dyndns.org/sambru/") [ ]("http://tuxmobil.org/links.html") is a Perl script that talks to a Samsung SCH-6100 or SCH-8500 cellular phone. You can use it to back up and restore the phone book. It can save the data in either raw/native format or as vCard data so GnomeCard can be used to view and edit the data. 

 [h=2]E-Mail Clients[/h]  E-Mail clients like    [Evolution]("http://www.gnome.org/projects/evolution/") [ ]("http://tuxmobil.org/links.html")  and others offer vCard import and export features.

[https://developer.ubuntu.com/en/blog/2015/08/17/fast-thumbnailer-ubuntu/](https://developer.ubuntu.com/en/blog/2015/08/17/fast-thumbnailer-ubuntu/)

---

### Post by largewebsite on 2017-02-03
[https://pypi.python.org/pypi/PyVCF](https://pypi.python.org/pypi/PyVCF) - USE PYTHON FOR VCF

---

