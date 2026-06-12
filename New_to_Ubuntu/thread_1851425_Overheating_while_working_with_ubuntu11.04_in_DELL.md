---
title: "Overheating while working with ubuntu11.04 in DELL studio 1457"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by ksrsubramanian on 2011-09-28
Hi all,
      I am using both Ubuntu 11.04 and windows 7 in my laptop. There is overheating while working with ubuntu(why?) . My X sensors are sensing the temperature in Raedon as 80 deg to 90 deg aftersome time. I have a solved thread in which some hardware changes are made. But can i do some software changes that can reduce heating.... I tried this ...reduce the  frequency of processor using  the panel applet...but it didnt wrk out.......

:(


Thanks,
Kallis

---

### Post by Immolatus on 2011-09-28
try installing the catalyst drivers for Linux (they do exist). It sounds like your GPU is just running wide open all the time. This can happen with less than adequate drivers.

[http://www.amd.com/us/Pages/AMDHomePage.aspx](http://www.amd.com/us/Pages/AMDHomePage.aspx)

This is where I found them.

---

### Post by 2F4U on 2011-09-28
Is this a new laptop or is it older? If it is older, try opening the case and see if there is any dust in it. Dust may block the fans to do their work.

---

### Post by ksrsubramanian on 2011-09-30
Hi immolatus,
              Problem almost solved
              I installed the drivers as u said via        system/administration/Additional Drivers
              Before Installation of this driver my Xsensor shows two temp as follows
                             acpitz- around 80 deg
                             Raedon  -  around 90 deg
             After installation only one temp is shown (why?)
                             acpitz- around 65 deg 

As you can see the temp is  reduced comprehensively

But i still feel it is large...... is it the normal  temperature ? I am using  DELL STUDIO 1457  core i7
    

If it is not the normal temp.... is there any way of further reducing it??

Thanks

---

### Post by Immolatus on 2011-10-02
sorry so long for a reply. I believe this to be about normal. Given the size of the lappy (14") and the fact that it is running a "discrete" card instead of integrated. The GPU kicks out more heat than anything in a PC or notebook unless it's a sever then it would be the HDD blocks or PSU.

You can try scaling back some of the settings in Catalyst as this is the customary trick for clockers. Might even get you another 10C or so.

P.S. I think the critical temp for radeons is 90C so half of that under load should be ok.:guitar:

you view the radeon temp in Catalyst.

---

### Post by ksrsubramanian on 2011-10-03
Hi immo
    Its k pal, no sorrys pls...
     I have enclosed a screen shot of my  catalyst  window
    It seems there is no provision for viewing Raedon temp
   Based on my percerption with the previous one(b4 installing driver) its not 90 C ....i hope...


Also i want to know what are all the settings i want to change ....in the window.... to reduce the temp


Thanks,
kallis

---

