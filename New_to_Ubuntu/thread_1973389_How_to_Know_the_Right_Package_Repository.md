---
title: "How to Know the Right Package Repository?"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by NCMS on 2012-05-04
I have installed a new "NVidia Quadro 4000 2.0GB" card on Ubuntu 10.04 LTS, 
 
**but I dont know;**
1. waht is the repository responsible for it ? 
OR 
2. where to search 
OR 
3. how to download the latest drviers for it 
 
 
:confused:
 
Thanks N Advance

---

### Post by Paqman on 2012-05-04
Open the Additional Drivers tool, that should pick the right driver for your card.

---

### Post by NCMS on 2012-05-05
Where to find "Additional Drivers" on 10.04 LTS ?
 
Howerver, that was not my conern, what I meant; is there a way to search the Net or a certain Ubuntu site for that particular driver and know the exact Repositry to be used with the  [FONT=Calibri]**sudo apt-add-repository   ??**[/FONT]

---

### Post by Cheesemill on 2012-05-05
You shouldn't have to add a repository for it, you should use the default Ubuntu repositories.

I believe the you can find the 'Additional Drivers' tool in the System applications menu, alternatively just hit ALT+F2 and type jockey-gtk then hit enter.

---

### Post by oldos2er on 2012-05-05
> **NCMS said:**
> Where to find "Additional Drivers" on 10.04 LTS ?
 
Howerver, that was not my conern, what I meant; is there a way to search the Net or a certain Ubuntu site for that particular driver and know the exact Repositry to be used with the  [FONT=Calibri]**sudo apt-add-repository   ??**[/FONT]

If you're looking for an PPA with the latest Nvidia drivers, try [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
For more bleeding edge and possibly buggy drivers, see [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

To search for PPAs, I use google's advanced search to specify searching in launchpad.net.

---

### Post by NCMS on 2012-05-05
Thanks for the PPAs ..
 
Actually an expert friend helped me witht the drivers as follows;

[B]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo nvidia-xconfig[/B]

 
I was looking for a Search tool/place on Ubuntu.com or similar site, rather than Google. 
 
Howerver, many thanks for the tip of narrwoing the search to **launchpad.net**

---

### Post by oldos2er on 2012-05-05
> **NCMS said:**
> I was looking for a Search tool/place on Ubuntu.com or similar site, rather than Google. 
 

There's [http://www.googlubuntu.com/](http://www.googlubuntu.com/)
Not sure if there's anything else like this.

---

### Post by Paqman on 2012-05-06
> **NCMS said:**
> Where to find "Additional Drivers" on 10.04 LTS ?
 

It may be called "Hardware Drivers" on that version. But yes, the System menu would be the place to go looking.

---

