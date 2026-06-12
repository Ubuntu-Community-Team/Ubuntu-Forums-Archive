---
title: "Problems with &quot;starlink&quot;"
date: 2013-12-04
forum: New to Ubuntu
---

### Post by Simon4360 on 2013-12-04
Firstly, if this is in the wrong section, my apologies. I'm new!!

I'm using a program called starlink which is a package of tools used in astronomy. I'm having a problem with one of the command in a program called "ccdpack" within starlink.
When i type the "debias" command in ccdpack i get an error:

simon@simon-M848A:~/Documents/Mphys/2013-10-10/sdf$ debias

    DEBIAS
    ======
IN - List of input NDFs > '*'

!! Locator refers to an object 'IN' which no longer exists (possible
!     programming error or corrupted HDS container file).
!  DAT_TYPE: Error enquiring the type of an HDS object.
!  Unable to associate a group of NDFs with parameter IN.
!    Unable to obtain valid list of NDF names using parameter IN
!  DEBIAS: Error performing initial preparation of CCD data.
!  Application exit status SAI__ERROR, Error

I don't really understand what is going on here as i used the program for the same thing last week and it worked perfectly. I tried a reinstall of starlink before to no avail.

I tried a different command in ccdpack called "makeflat" which also makes use of this "IN" parameter and that works fine too so i assume it is a problem within the debias command.
I have tried to open this with gedit to see if i can see where "IN" is coded into it but it seems unwilling to open.

Any help would be greatly appriciated

Simon

---

