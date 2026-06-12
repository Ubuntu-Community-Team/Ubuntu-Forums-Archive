---
title: "Writing in Hebrew in Libreoffice"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by maringouin2 on 2014-02-19
I write mostly in English but need to insert Hebrew text from time to time. I have a dual-boot system; in Windows 7 I have LibreOffice 4.1.5; in Ubuntu Precise Pangolin I have LibreOffice 3.5. LibreOffice's relevant Hebrew packages are installed in both systems, as are Hebrew fonts.

I have followed all the instructions I could find, and ticked all the boxes under Language--enable CTL, default CTL language = Hebrew, etc., etc. I do NOT EVER check the 'for the current document only' box. I have Hebrew fonts installed and selected under the LibreOffice Writer settings. 

But two things: (1) Hebrew doesn't EVER show up as one of the languages available under Tools - Language - for Selection/Paragraph/All Text;

and (2) when I close the document, the CTL settings disappear and I have to start all over again in the next document (not that they're working, but still).

I haven't been able to find any information online about this. LibreOffice's documentation only deals with globally changing the default language for the programme. Can anyone help me? How do I get Hebrew into an available language 'for selection'?

Many thanks.

---

### Post by grahammechanical on 2014-02-19
Have you installed a Hebrew keyboard layout? In addition to English I also have a Greek keyboard layout and in Libreoffice Writer when I go to Tools>Language>For Selection I see Greek in the list.

Because I have the Greek keyboard layout I do not need to use Libreoffice Tools>Language>For Selection. I just click the keyboard layout icon in the ubuntu top panel and change from English to Greek and I can type in Greek. I am sure that I could do the same with Hebrew. We should not need special Hebrew fonts. The standard Unicode fonts in Libreoffice should do the job.

Here we are, a Hebrew keyboard layout.

/'&#1511;&#1512;&#1488;&#1496;&#1493;&#1503;&#1501;&#1508;][&#1513;&#1491;&#1490;&#1499;&#1506;&#1497;&#1495;&#1500;&#1498;&#1507;,\<&#1494;&#1505;&#1489;&#1492;&#1504;&#1502;&#1510;&#1514;&#1509;.

on a qwerty English keyboard. Now Greek

;&#962;&#949;&#961;&#964;&#965;&#952;&#953;&#959;&#960;[]&#945;&#963;&#948;&#966;&#947;&#951;&#958;&#954;&#955;\«&#950;&#967;&#968;&#969;&#946;&#957;&#956;,./

Just by changing installed keyboard layouts. Once I type into a Libreoffice Writer document with that Hebrew keyboard layout it then appears in Tools>Language>For Selection.

Regards.

---

### Post by maringouin2 on 2014-02-20
Thank you for this, Grahammechanical. It works. It took me a couple of tries (and I answered your question wrongly first, so I've edited my reply) but I've got it now. The one additional thing I found is that I had to make a new default document template which includes the Language settings, otherwise they disappear when I close the document and I have to start again in each new document. This is great. Thanks for being so prompt in your reply.

---

### Post by Buntu Bunny on 2014-02-20
I've been wondering this same thing, so let me add my appreciation grahammechanical. Thanks.

And maringouin2, let me welcome you to the Ubuntu Forums.

---

