---
title: "Can't configure wireless printer with network"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by elderrich on 2013-01-27
I haven't been able to configure my new Dell laptop (with Ubuntu 12.04)  to connect wirelessly with my new Brother HL-2270DW printer. When I use the Brother printer installation CD, it doesn't ask for my wireless network settings and doesn't recognize my existing wireless network. I read that this printer is supposed to easily work with Linux. Is this a printer issue rather than an Ubuntu one?

---

### Post by ajgreeny on 2013-01-27
I would be very surprisded if the CD you have has any Linux driver software on it, unless things are starting to change markedly since I had to set up a Brother MFP.

To get that working I had to download driver software from [http://www.brother-store.co.uk/category/brother-linux-drivers_MjQyMQ==.html](http://www.brother-store.co.uk/category/brother-linux-drivers_MjQyMQ==.html) which was in the form of .deb packages.  Have a look there to see if you can find what you need.

---

### Post by kurt18947 on 2013-01-27
Hi

There is also an installer script which I have had very good luck with.  I recall the HL-2270DW printer required a patch when using the normal Brother .deb files.  Here is a link to the Brother installer script:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

I didn't find using it exactly intuitive:rolleyes:  but once I figured it out it has worked quite well.  I have not tried the installer on the HL-2270DW but it has worked well on several MFC- machines.  Good luck.

---

### Post by gifford on 2013-01-27
Go to the Brother site: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
 
Take your time in setting up, follow the instructions for network printing.
Post here again if you have any problems.

---

### Post by pdc on 2013-01-27
if we sort of go backwards, and cover how to configure the scanning side of the Brother MF devices;

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html)

and post #9 from here

[http://ubuntuforums.org/showthread.php?t=2039840](http://ubuntuforums.org/showthread.php?t=2039840)

having installed the brscan4 driver used the command

> brsaneconfig4 -a name=DCP-7065DN model=DCP7065DN ip=192.168.1.201


where the poster explained that "The 201 is just my internal, DCHP-assigned Brother ethernet IP."

he checked the install with 

> brsaneconfig4 -q | grep DCP-7065DN

and "It came back looking happy, including my internal IP address."

Printer install

this page

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

talks of network install: 

> Step 5b. (for Network Connection) Configure your printer on the cups web interface
    5b-1. Open a web browser and go to "http://localhost:631/printers". 
    5b-2. Click "Modify Printer" and set following parameters.

    - "LPD/LPR Host or Printer" or "AppSocket/HP JetDirect" 	     	for Device
    - lpd://(Your printer's IP address)/binary_p1 	     	for Device URI
    - Brother 	     	for Make/Manufacturer Selection
    - Your printer's name 	     	for Model/Driver Selection

and gives this example of what a configured network printer looks like in CUPS

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#cwi_img2](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#cwi_img2)

___________________________________________________________

here is a YouTube video on how to configure a network printer

[http://www.youtube.com/watch?v=YekdBoF7vlY](http://www.youtube.com/watch?v=YekdBoF7vlY) 

is this helpful?

---

