---
title: "Configure Bluetooth Modem in Ubuntu"
date: 2009-06-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Nizar on 2009-06-28
**How do I -- Configure Bluetooth Modem in Ubuntu**


Mobile phone today come with Bluetooth as standard feature, and in most of these phones, modem is also present which allows Internet surfing over computer. Unlike Windows XP, a Bluetooth phone can be configured in Ubuntu without having to install manufacturer supplied CDs or driver. This guides walks through this process. Here's how:

 

Note before you start:

   1.

      A working GPRS connectivity is required on handset. Activate and test GPRS over phone before attempting this guide.
   2.

      In case of Nokia phones (2630 and 2760), an additional Access Point definition is required under phone menu Settings > Connectivity > Packet Data > Packet Data Settings > Edit Active Access Point, and then select the same in Active Access Point.
   3.

      Watch out for the charges as usually its per MB – its advisable to turn images off when not needed.
   4.

      This guide is tested with Ubuntu 7.10 (Gutsy) – and should run over newer versions without modifications - using basic phones -- Sony Ericsson K320i and Nokia 2630 – over Acer 5573 laptop

 

**Step 1 - Check the Bluetooth availability on PC**

Login as root user. Enter the following command in Terminal to check the Bluetooth device in PC is up and running:

 

 

```
hciconfig
```


Typical output displays type, address and other preliminary information as shown below:


```
hci0: Type: USB

BD Address: 00:19:7E:DF:51:02 ACL MTU: 1017:8 SCO MTU: 64:8

UP RUNNING PSCAN ISCAN

RX bytes:957 acl:0 sco:0 events:26 errors:0

TX bytes:603 acl:0 sco:0 commands:26 errors:0


``` 

This shows the PC has a Bluetooth adapter up and running.

 

**Step 2 - Scan for the phone**

Keep the phone's Bluetooth setting as discoverable and enter the following command in Terminal:


```
hcitool scan
```


This displays phone's name MAC address (note it down for future use) and name as shown below:


```
Scanning ...

00:1C:A4:96:03:CC K320i


``` 

 

[B]Step 3 – Verify if DUN (dial-up networking) profile exists
[/B]
Use the following command to browse phone's Bluetooth profiles:


```
sdptool browse 00:1C:A4:96:03:CC


``` 

Note that the address is used from the previous step. If DUN exists, it would be listed along with other profiles as follows:

 

```
Service Name: Dial-up Networking

Service RecHandle: 0x10002

Service Class ID List:

"Dialup Networking" (0x1103)

"Generic Networking" (0x1201)

Protocol Descriptor List:

"L2CAP" (0x0100)

"RFCOMM" (0x0003)

Channel: 2

Profile Descriptor List:

"Dialup Networking" (0x1103)

Version: 0x0100


``` 

Note down the channel value for future use (which in this case is 2).

 

[B]Step 4 - Set an easy to remember passkey (optional)
[/B]
Edit the file /etc/bluetooth/hcid.conf and set the passkey to four times zero in Options section. This is done only to make the passkey easier to remember, otherwise any passkey can be set here.

 

```
# Default PIN code for incoming connections

passkey "0000";


``` 

Also ensure that rest of the settings have following values:


```
autoinit yes;

security auto;

pairing multi;

```

**Step 5 – Edit the RFCOMM file**

Edit the file /etc/bluetooth/rfcomm.conf to bind the DUN channel over the discovered phone with RFCOMM which will be used later for connectivity. Ensure that the file looks like the following:


```
rfcomm0 {

bind yes;

device 00:1C:A4:96:03:CC;

channel 2;

comment "Example Bluetooth device";

}


```
Note that the values of device and channel entered here are the ones noted down earlier in step 2 and 3 respectively.


**Step 5 - Restart Bluetooth**

Enter the following command:


```
/etc/init.d/bluetooth restart
```

 

The ouput is:


```
* Restarting Bluetooth services [ OK ]

```
 

**Step 6 – Perform paring**

Using the search device option on handset, scan for the PC and enter the passkey from step 4 in handset to complete pairing. Successful pairing means PC and device have authenticated each other for further interaction.


**Step 7 – Configure wvdial and connect**

Edit the file /etc/wvdial.conf and add a new Dialer entry with service provider specific settings (ask your service provider for phone number, username and password). The new dialer entry look like following:

 

```
[Dialer service-name]

Modem = /dev/rfcomm0

Phone = ATD*99***2#

Username = service-username

Password = service-password


``` 

Replace the service-name, service-username and service-password with actual values as communicated by the service provider.


Use the dialer named defined to connect to the Internet in Terminal window, for e.g.:

 

```
wvdial service-name
```


And enjoy surfing!

**Note for backup and restore:**

Note: Make a copy of all the files used in this tutorial (e.g. rfcomm.conf) so that they can be restored if required. 

Backup - Use the following command in Terminal window to first go to relevant directory, and create a copy of the file before editing it. For example, in case of rfcomm.conf file, here's how to create backup file:

```
cd/ root
cd etc/bluetooth
cp rfcomm.conf rfcomm.conf-backup


```

Restore - Use the following commands to first delete the existing file and restore the backup copy.

```
rm  rfcomm.conf
cp rfcomm.conf-backup rfcomm.conf
```

---

