---
title: "HOWTO: Remote Administration through a firewall"
date: 2008-04-02
forum: Outdated Tutorials &amp; Tips
---

### Post by talcite on 2008-04-02
This guide was written from the results of administering my younger brother's system in a University residence from my house. It is not designed for beginners and assumes that the system maintainer will be reading this. The actual use by the user is designed to be as simple as possible.

The key to establishing a remote administration connection through Vino (Gnome remote administration) and to bypass a firewall is to use a reverse SSH tunnel.

Terminology used in this guide:
**Admin**: Presumably you, the person who will be performing the administration.
**User**: The person who's system you will be administering. 
**server**: Your system. You will be receiving the ssh connection on this machine.
**client**: The machine that you will be performing administration on.


The reverse SSH connection requires that the server have an open sshd (ssh daemon) connection. However, sshd connections are dangerous if not managed correctly and care must be taken to safeguard against unintended connections. 

*Aside*
The details of the setup are as follows:
The use of a dynamic IP greatly increases security, so the user will be asked to contact the admin and to obtain the admin's IP address.

The port will be determined beforehand when the admin is configuring the user's SSH script. This will not change since the admin must have the proper ports open/forwarded on the server. A port in the 20 000 range and above is ideal.

The admin starts the sshd script only when the user is asking for help.

The combination of the two will hopefully create a situation where the chances of an unwanted intrusion onto the server will be minimized. 
*Aside Finished*

There are the steps to follow in order to set up the reverse ssh tunnel.

Ensure that ssh is installed onto the client system and sshd is installed on the server. There are many guides out on google and in the forums to do this. Also, for an extra layer of added security, use RSA or DSA keys for to authenticate and disable password logins over sshd. Here are very good guides to accomplish that:

[http://sial.org/howto/openssh/publickey-auth/]("http://sial.org/howto/openssh/publickey-auth/")
[http://www.ibm.com/developerworks/library/l-keyc.html]("http://www.ibm.com/developerworks/library/l-keyc.html")

Copy this script into a .sh file and make sure that the MAINTAINER, PORT, and USER variables are properly configured. Make sure that the proper permissions are included on the client machine to execute the script (755 would be nice).

```

#!/bin/bash
# Use this when you need help from Matt
# Remember to change the maintainer name variable and to choose a random port!

MAINTAINER="Matt"
PORT=12345
USER="Chris"

echo -e "Instructions:\n"
echo -e "This script will allow" $MAINTAINER "to connect to your computer and bypass the \nUniversity firewall. You must leave this running while he is connected. \nAfterwards, you MUST also close this window to make sure the connection \nis closed.\n======\n"

echo -ne "Call" $MAINTAINER "and ask for his IP Address. Type it in now. When finished, hit [Enter] \nIP= "

read IP

echo -n "Is this correct? (Y/n) "

read CHECK

if [ $CHECK == "y" -o $CHECK == "Y" ];
then
	sudo ssh -L 5900:$IP:5900 -l $USER -p $PORT -N $IP	
else 
	echo "exiting."
	exit 1;
fi


```

Put this script onto the client machine and link it to the desktop or toolbar. 

Configure the server to accept sshd connections and from the port that you specified in the script. **Reminder:** forward the ports on your firewall/router.

Create a script on the server to start the sshd daemon when needed. Make sure sshd shuts down after you are finished helping the user. 

And Voila, that's it. You now have a reverse SSH Tunnel running and configured. You can now set up Vino(System->Preferences->Remote Desktop) as usual and bypass the firewall. 

updates:
I will post the server script when I get back home.

---

### Post by KubuntuKilledMe on 2008-04-03
This solution is good and it works. However i believe the more canonical (hah) solution for this situation is a vpn like OpenVPN.

---

