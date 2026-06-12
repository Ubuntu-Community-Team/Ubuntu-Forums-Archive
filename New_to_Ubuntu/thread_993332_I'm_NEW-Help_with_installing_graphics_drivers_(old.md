---
title: "I'm NEW-Help with installing graphics drivers (old ones)"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by scorpiotail on 2008-11-25
I'm new at using Linux, hence the reason I am here.  I need some help with installing a particular driver.  I have read some pages for assistance, but it looks like I have to use the terminal and I don't want to mess up anything.

I'm trying to install drivers for my Mobility Radeon 9000 so the graphics will stop being choppy.

I'm using Ubuntu 8.10.  Much thanks.

---

### Post by porchrat on 2008-11-25
Personally I would recommend you look up which driver to use on the ati graphics drivers website.  The catalyst drivers actually have an install program like Windows drivers have.

REALLY easy.

Just go to [this]("http://ati.amd.com/support/driver.HTML") page and enter your operating system, and card details.

After you have downloaded the file to your desktop then you will need to use the command line for two things and that is it.

You will need to type:

```
chmod u+x ~/Desktop/name_of_file
```

you then type this:

```
sudo ./name_of_file
```

Where "name_of_file" is the name of the ati installer program (should end with .run)

---

### Post by bhadotia on 2008-11-25
> **porchrat said:**
> 

You will need to type:

```
chmod u+x ~/Desktop/name_of_file
```

you then type this:

```
sudo ./name_of_file
```

Where "name_of_file" is the name of the ati installer program (should end with .run)

You mean:
```
sudo chmod a+x ~/Desktop/name_of_file
```
coz you are using sudo to execute it.

---

### Post by porchrat on 2008-11-25
> **bhadotia said:**
> You mean:
```
sudo chmod a+x ~/Desktop/name_of_file
```
coz you are using sudo to execute it.

Good point thanks for picking that up.

As bhadotia says use chmod a+x in place of chmod u+x.

This will add execute permissions to the file allowing _all_ users to execute it.

---

### Post by andrew.mckevitt on 2008-11-25
> **scorpiotail said:**
> I'm new at using Linux, hence the reason I am here.  I need some help with installing a particular driver.  I have read some pages for assistance, but it looks like I have to use the terminal and I don't want to mess up anything.

I'm trying to install drivers for my Mobility Radeon 9000 so the graphics will stop being choppy.

I'm using Ubuntu 8.10.  Much thanks.

You could try 'envy', it got the mobility graphics working in my old compaq.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

no terminal experience needed, unless it goes horribly wrong, brings back memories of the good old days trying to get my geforce2 card working.

If it does all go wrong and you cannot get back to a gui.

sudo dpkg-reconfigure xserver-xorg

should set it back to default.

---

