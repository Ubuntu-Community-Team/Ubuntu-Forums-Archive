---
title: "adding a font using nautilus and make it available to all users"
date: 2006-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by rioguia on 2006-10-18
NOTE:  You should be able to cut and paste the terminal commands below except that you need to modify the terminal command for step 4 by replacing user_name with your actual user name.  Make sure you include the "&" at the end of some of the commands.  This allows you to open multiple instances of nautilus from the same terminal.  Also, the font in this example was downloaded from: [http://www.muq.org/david/tempus.htm](http://www.muq.org/david/tempus.htm)
[B]
1. Open a terminal.[/B] 
Applications/Accessories/Terminal

**2. Now lets navigate from your user's home folder to the user's Desktop.**
cd Desktop.  

**3.  Unzip the font you downloaded to your desktop.  In this example we will use Tempus Sans ITC.**
unzip tempsitc.zip

**4. As root open nautilus at the desktop folder where you unzipped the font.**
sudo nautilus /home/user_name/Desktop &

[COLOR="DarkRed"]*You should now see a font file with an icon named something like TEMPSITC.TTF. *[/COLOR]


**5. As root open another instance of nautilus in the fonts location.**
sudo nautilus fonts: & 

**6.  Drag the TEMPSITC.TTF icon (from your first nautilus instance) to the fonts location(in your second nautilus instance).**[IMG]http://www.substantis.com/images/add_a_font.png[/IMG]

**7.  Now reload the fonts cache so you can use font immediately and you are done (be patient this may take a while).**
sudo fc-cache -f -v

---

### Post by hikaricore on 2006-10-19
Ty for this info, now I know how to install the 634 fonts I sent myself at work on the ubuntu desktop publishing system I'm working on.  hehe

I've been too lazy for the last two weeks to look into it.  =)

---

