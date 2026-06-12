---
title: "New characters and short-cuts in LibreOffice (Sanskrit Romanization)"
date: 2017-02-27
forum: New to Ubuntu
---

### Post by angelaar on 2017-02-27
Dear all,

though not new to Ubuntu per se, I am very new to working with the terminal and anything that surpasses basic stuff on a direct interface. 

At the moment I am trying to install some diacritic markers for romanizing Sanskrit in LibreOffice (without using "Insert special characters" or long codes). My LibreOffice version is 4.2.8.2, running in Ubuntu 14.04.5 LTS. Installation of the desired characters and short-cuts has been explained elsewhere in an (apparently?) workable manner:

"1. Download the attached zip file
2. unzip (become a folder named "user")
3. move and overwrite the folder /home/USER_NAME*/.config/libreoffice/4/" (source: [http://thanhsiang.org/faqing/node/203](http://thanhsiang.org/faqing/node/203))

After hours of support forums and getting to know the terminal, I finally gathered a very basic grasp of some of the commands. I overwrote as follows:

      anon@anon-SVS1313H1ES:~$ rsync -a ~/Desktop/user/ ~/.config/libreoffice/4/
     anon@anon-SVS1313H1ES:~$ 

I used rsync because the old folder contains far more than the new one does, and the latter is surely meant to complement, rather than fully replace it. Nevertheless, I actually think the author of the above quoted instructions made a mistake and the destination directory should rather be ~/.config/libreoffice/4/user/ instead. Either way, although the overwriting appears to have worked in both cases, neither affected the desired result. That result should be that Alt Key + a = &#257;, Alt Key + W = &#347;, and so on. In LibreOffice Writer Alt Key + a however still opens the "Table" drop-down menu, etc. 

Is there something I should still do to enable these now latent short-cuts, or is something else the matter? I also have a German keyboard layout, which perhaps is a factor (a Sony Vaio). I would be really grateful for some help. I am at my wits' end and put in a frustrating amount of time already, considering I am not even a Sanskritist!

All best,
Leo

---

