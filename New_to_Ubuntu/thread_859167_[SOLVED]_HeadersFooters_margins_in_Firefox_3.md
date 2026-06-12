---
title: "[SOLVED] Headers/Footers margins in Firefox 3"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by septekin on 2008-07-14
Hello Folks,

Now and then I would like to make a paper print of a web page. And I can. However, since I replaced my HP Deskjet printer a few days ago with a model D2460, the header prints only the bottom millimetre of the line, the footer does not print out at all. File -> Print View displays the page as it should be. The Margins settings of Firefox -> File -> Page Setup... change the main part of the page, without altering the header or footer. I believe this is due to the internal settings of the printer as the old printer did print these correctly; my B&W laser prints them out correctly. I have tried A4 and A5 size papers, both display the same problem.

I wonder if there is a setting either somewhere in Firefox or in Printers that would enable me to correct the issue, or am I stuck with a stupid printer?

I have no intention to boot into XP to see what happens there - I'm only keeping it in this machine in case I have to read a years old MS Works (.wks/.wpd) or PaperPort (.max) file!

Any suggestions, please?

	(Deskjet D2460 Properties:
	 Model:  Deskjet d2400
	 Driver: hpijs, hpijs 2.8.6.20)

---

### Post by silkstone on 2008-07-14
System > Administration > Printing > Job Options tab.

Scroll down and try increasing the top and bottom margins.

---

### Post by septekin on 2008-07-14
silkstone, thanks for the quick reply.
However, S > A > Printing gives me 3 tabs: Printer, Edit and Global Settings. I could not find Job Options anywhere. I should have known better than not specifying my system: I'm running the old Feisty on this machine, an HP Pavilion ZV6000 series, simply because it would not install Gutsy and I'm reluctant to install Hardy.

Can you help further?

---

### Post by silkstone on 2008-07-14
Ah, right - that must have changed in Hardy. Is there anything useful in Global Settings? That's basically what Job Options is - defaults for various settings if the application doesn't force its own.

---

### Post by septekin on 2008-07-14
No, nothing for this.

To find out what you were talking about, I just installed the same printer on my mobile laptop which has 7.10 and 8.04 installed. Yes, I found the Job Options in Gutsy (my default here) where I added Header margin 18 points, logged out and in: same problem. I shall now go and have a look in /etc/cups/ppd and do some editing (after a good backup, of course).

Thanks again for your suggestion. If you can think of anything else, please let me know.

Cheers.

---

### Post by silkstone on 2008-07-14
Something else to try, but be careful with this as I can see that it can be altered but I'm not sure what the values should be!

In FF type about:config in the address panel.

Search for 'print'.

You'll see a load of general settings and maybe some for your specific printer. Some of these refer to margins. You could try changing them (make a note of what they were!) and see if it makes any difference.

P.S. You have to restart FF after any changes.

---

### Post by septekin on 2008-07-14
Yes, that`s it! The entry was ...print_edge_top, changed from 4 to 16. I still cannot print the footer but I expect it is a matter of finding the right combination of _print_edge_bottom and bottom margin in page setup. I shall keep the thread open for a while in case I have to come back for further advise. Thanks a lot silkstone.

---

### Post by silkstone on 2008-07-14
I'm glad we're getting somewhere!

---

### Post by septekin on 2008-07-14
Not "we" silkstone, you!

I believe the configuration uses a mixture of millimeters, inches and points. The truth downed on me when I noticed that the page margins I'd entered in millimeters were shown in decimal fractions of an inch. print_edge_bottom, left, right and top must be in points. When I modified the bottom figure to 48 the footer started printing out.

Once again, thank you for your competent help. I can now happily close this thread.

All the best.

---

### Post by AlexanderDGreat on 2010-03-18
Margins not working for me, using Jaunty FF 3.0.18

I created a simple report from my php+mysql website. Now I want to print it so from FireFox, I go to File -> Print -> Print Preview -> then all your hidden buttons show up, thanks! Then I adjust my Paper Type: Letter, Legal or A4, no problems.

But when I adjust the Margins on these papers, I hit APPLY, boom! The settings are DISRESPECTED! They aren't applied. The Paper Type is working fine, but the Margins are a nightmare!

Do you know any solution to this? I tried this on Windows used Firefox same version, did the Page Setup, Margins = 0 on all sides then it works like a charm, no hassles!

Is this Ubuntu's poor Page Setup implementation?

It's very frustrating.

Not only that, so suppose I'm done with Page Setup, I will Print it now, I hit "Print" the go to Options -> Remove the URL, Date/Time, # of Pages, Title, etc... of my webpage, I print ok. But when I print the same document again, I have to REDO all the Print Options, it doesn't get saved.

It's a mess, I've been reading a lot about it, and there aren't as much people talking about this. Pls. help! Thanks for reading.

---

