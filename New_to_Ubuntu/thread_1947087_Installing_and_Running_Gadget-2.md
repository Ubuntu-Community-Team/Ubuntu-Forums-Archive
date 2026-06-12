---
title: "Installing and Running Gadget-2"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by meballav on 2012-03-26
Hi, I am beginner user of ubuntu. Our teacher told me to try to install Gadget-2 in ubuntu but i cant. I have downloaded **Gadget 2.0.7, GNU scientific library, FFTW,MPICH, and HDF5 **but i was unable to install this files and runing the Gadget2. so do any body help me please i need your help.

---

### Post by Rodney9 on 2012-03-26
Please use the commands  `gunzip gadget-2.0.7.tar.gz' and  `tar -xvf gadget-2.0.7.tar' to unpack the files. You will obtain a directory `Gadget-2.0.7/' , and various subdirectories containing the actual source code, the code documentation, as well as a number of simulation examples and very basic analysis scripts. Please refer to the** README **file, and **GADGET's User's Guide** for further directions about installation and usage. A brief guide to parameters in the Makefile and the parameterfile, as well as a cross-referenced source code documentation is accessible with a web-browser in the `html/'-subdirectory (open the  `index.html' file). Note that the large size of the download is caused by the included example initial conditions.

---

### Post by meballav on 2012-03-26
thanks you very much.
i have read the instruction but i am not able to install HDF5 so could you help me how to install this.
i searched in net for help i found few but it does not work as in HDF5 there is no configure file to configure at first. so please help me if you know how to install it.

Ballav mani dahal
kathmandu Nepal

---

### Post by raguelmoon on 2012-11-11
> **meballav said:**
> thanks you very much.
i have read the instruction but i am not able to install HDF5 so could you help me how to install this.
i searched in net for help i found few but it does not work as in HDF5 there is no configure file to configure at first. so please help me if you know how to install it.

Ballav mani dahal
kathmandu Nepal

Dear Ballav,
Please read this :
[http://astrobites.com/2011/04/02/installing-and-running-gadget-2/](http://astrobites.com/2011/04/02/installing-and-running-gadget-2/)

Cheers,
Ram

---

