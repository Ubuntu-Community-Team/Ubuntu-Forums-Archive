---
title: "Network Printer"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by czgirb on 2012-04-18
Currently I give a Lucid a try ... please guide me.
Now, I wish to use a printer, Canon Pixma iP1880, which connected through LAN.
How to do it?
Please guide me ....

---

### Post by anejo on 2012-04-19
select add a printer... (obviously)
then select find a network printer (from the list of options)
select the one that you want to use
Lucid 99% of the time will find the right driver but
you have to negotiate your way to the make and model
once the driver is selected, you could print a test page...

---

### Post by czgirb on 2012-04-19
I used:

**System** > **Administartion** > **Printing** > click the **Add** > select **Find Network  Printer** > fill **Host**, and click **Find** > **Canon**, but the available driver to choose is start with **Pixma iP2000** only, no **Pixma iP1xxx**?
So I forced to use Pixma iP2000 ... and print out a **Test Page** ... but nothing happen with the printer.

Please guide me ...

---

### Post by newbie-user on 2012-04-19
Canon, as far as I know, doesn't release Linux drivers for its products. This leaves you with a few options.

1) Ask Canon to release Linux drivers
2) Try a newer version of Ubuntu
3) Find a third-party driver for your printer

At my work, we have Canon imageRunner copiers and we have to get third-party Linux drivers from a company called CodeHost.

---

### Post by kurt18947 on 2012-04-19
Possible help here:

[http://www.unixmen.com/install-canon-pixma-ip1880-in-linux/](http://www.unixmen.com/install-canon-pixma-ip1880-in-linux/)

---

### Post by HiImTye on 2012-04-19
the Canon CD likely came with printer drivers and scanner drivers if it is also a scanner.
otherwise you can download them from their website or add their PPA

---

### Post by ixtok on 2012-04-19
Google Canon-Asia and go to their support area. Choose your printer or the printer series closest to it. You should find a printer driver for debian distros. Download driver, un arc file. Using the terminal, and dir and cd commands navigate to the directory where the driver was un arced, you should find a file "install.sh". In the terminal type ```
sudo ./install.sh
``` and you will be given a couple of choices and hopefully this will set your printer up.

---

### Post by czgirb on 2012-04-19
> **kurt18947 said:**
> Possible help here:

[http://www.unixmen.com/install-canon-pixma-ip1880-in-linux/](http://www.unixmen.com/install-canon-pixma-ip1880-in-linux/)

This URL is lead me to install printer for my computer.
But what I want to use the printer, which installed previously in others computer.
Is it the same?

---

### Post by anejo on 2012-04-19
> **czgirb said:**
> **Printing** > click the **Add** > select **Find Network  Printer** > fill **Host**, and click...
Why did you fill in a host?
That is not necessary IF you are already authenticated on a domain where there are LAN printers. When you select the 'Find Network Printer' you need to wait for the system to identify what is available to you. A list of IPs and printers will appear above the 'Find Network Printer' line. You select accordingly and follow the instructions above.

---

### Post by kurt18947 on 2012-04-19
> **czgirb said:**
> This URL is lead me to install printer for my computer.
But what I want to use the printer, which installed previously in others computer.
Is it the same?

If I understand you correctly, yes.  You must install the printer drivers onto each computer that wants to use that printer.

---

### Post by czgirb on 2012-04-19
> **anejo said:**
> Why did you fill in a host?
That is not necessary IF you are already authenticated on a domain where there are LAN printers. When you select the 'Find Network Printer' you need to wait for the system to identify what is available to you. A list of IPs and printers will appear above the 'Find Network Printer' line. You select accordingly and follow the instructions above.

How to authenticated on a domain?
Maybe I'm not.
Please guide me.
Thanx

---

