---
title: "HOWTO: Tiny Print to WinXP Printer."
date: 2004-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by burque on 2004-11-01
Very small and incomplete. Does not address known OpenOffice printing problems. This procedure enabled me to print from console and Firefox. Other programs most likely work too. Printed image is shifted incorrectly, but that is likely another issue.

1) Make sure your WinXP printer is shared: Start -> Settings -> Control Panel -> Printers and Faxes; highlight your printer and right click. Click on "Sharing . . .";
on "Sharing" page click radio button "Share this Printer". You don't need a password, but you DO need a share name (for me DCP-1000). This will be important to know when setting up from your Ubuntu machine.

2) Back on Ubuntu, assuming you're logged in as yourname, open a console;
execute "su root" and enter your root password. Execute "smbpasswd -a yourname". I haven't tried this, but if you don't have a root user enabled, try "sudo smbpasswd -a yourname".

3) From the Ubuntu desktop, click on Computer -> System Configuration -> Printing. If your printer is not there, add it (not covered in this HowTo). On the "Connection" tab enter the share name from the XP box (for me, DCP-1000), and for user name and password, enter "yourname" (assuming you're logged in as "yourname" and then the password you picked in step 2. Change the page sizes, etc. as necessary. Back on on the "Connection" tab, click on "Print a Test Page". Hopefully all is well.

4) If you re-enter the configuration dialog the user name and password will be gone. However, for me this DID NOT affect the ability to print a test page. I WAS NOT able to print a test page until I entered the smbpasswd password along with my user name, but after that I could print.

5) Search the forums here and you will discover that there are issues with Openoffice.org. I have not resolved them at this point, and defer to the experts.

Regards,
burque

---

### Post by mr_ed on 2004-11-02
Yes, sudo smbpasswd -a "yourname" works.

---

