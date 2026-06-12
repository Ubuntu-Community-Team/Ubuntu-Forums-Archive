---
title: "timeout in Xauthority"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by munder on 2008-06-20
Hi

I need to have an openoffice service running headless (i.e. without a display) and owned by www-data. I'm root, so I execute a script with su www-data -c "the script".

My script contains the following:

#location of Virtual Frame Buffer X Server (Xvfb)
Xvfb_CMD=/usr/X11R6/bin/Xvfb

#Virtual Display which OpenOffice.org will open under
VIRTUAL_DISPLAY=":20"

#Xauth program
XAUTH=/usr/bin/xauth

#mcookie program
MCOOKIE=/usr/bin/mcookie

[snip]

# Start Xvfb
	if [ -x $Xvfb_CMD ]; then
		
		#If user has $XAUTH, then set authorizations
		 if [ $XAUTH ]; then
			echo "Setting authorization on local display $VIRTUAL_DISPLAY.0"
			#Give authorization to access this Virtual Display
		        $XAUTH add $VIRTUAL_DISPLAY . `$MCOOKIE` > /dev/null

At that point, I get the message:

/usr/bin/xauth:  timeout in locking authority file /root/.Xauthority

If I run the script as root, I have no problem.

Once the OO service is running, routines to automate OO are called from a PHP page. If the start-up script had been run as root, that will work. However, if it had been run as www-data, it won't work, even though the OO process is shown as being owned by www-data. I assume that that's because the timeout problem meant that OO has no "display" (I gather it needs to have one, even if it's an invisible virtual one).

I know next to nothing about Linux, I'm afraid, but I do need to have this stuff running on a Linux server eventually. Currently I'm testing it on Ubuntu Hardy. I've read up a bit on Xauthority, but I can't see how to overcome this problem. 

Any ideas?

Thanks in advance.

Mick

---

