---
title: "Mini HowTo - WPA connection on demand"
date: 2010-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by seydou on 2010-03-10
***WPA connection on demand - Mini HowTo for UBUNTU users***

I put this guide together while being on extensive travels. In many occasions, I got connected through the router using WPA/WPA2 certification program, using PSK mode (pre-shared key), which is the method prevailing to obsoleted WEP. You can find more info on WPA at [http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access), as going into further details is beyond the scope of this article. I do not cover the installation of the driver as well, so make sure you have it up and running before you go any further. Google is your friend here. The main purpose of this mini how-to is to put across the most straightforward and simplest way to establish quick connection on demand. It is fairly easy under Linux, if you are not scared of typing commands in terminal window. I found it more flexible, and far more easy than any GUI application (wpa_gui, for example). 

**Software needed**

[LIST]
[*]wireless-tools - essential package for WI-FI management, most likely installed by default
[*]dhcp3-client - default install as well, used to request IP from the router
[*]wpasupplicant - handles the assotiation using WPA passphrase
[/LIST]

Optionally, you can consider wicd - it provides neat graphical interface to view and manage Wi-Fi connections. I did not manage to connect using WPA/WPA2 with this tool, but you might use it to view available routers and their encryption schemes.

To install, just run this at the command prompt:

```
sudo apt-get install wireless-tools wpasupplicant dhcp3-client
```

**Preparing device and configuration files**

First, check what devices we have for use

 ```
iwconfig
```

The output can look like this:


```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

The last one is the one we need, yours might be different, but for the sake of simplicity, we will go ahead with wlan0.

Now, let's examin the contents of /etc/network/interfaces. It should contain this and only section for wlan0:

```
  auto wlan0
  iface wlan0 inet dhcp

```

It is the bare minimum, you do not need anything more in order to connect on demand. Needless to say, that you need to be root in order to edit this file, or you can use sudo to get the write access:

```
sudo vi /etc/network/interfaces
```

Having fixed the basic configuration, take a look at the devices to confirm if wlan0 is up:

```
ifconfig
```

If you can not see wlan0 in the output, bring it up with this:

```
sudo ifconfig wlan0 up
```

Now, we must have the passphrase and the name of the router (ESSID). Passphrase is to be obtained from the router maintainer or owner, which can be the biggest challenge, especially if you are at friend's house. If your friend is less savvy, chances are he or she does not have a clue what the pass-phrase they use is. In this case, you probably might look for another router ;-). Anyway, let's assume we have the pass-phrase for our example. If unsure about ESSID, have a look what is in the air:

```
sudo iwlist wlan0 scan
```

Output differs from your driver, but should look more or less like this:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:9F:D6:ED:8D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"MYWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000011557ce18b
                    Extra: Last beacon: 1224ms ago
                    IE: Unknown: 000D54686F6D736F6E393642353339
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```


If there are more cells, the output labels them Cell 01, Cell 02 etc. Output also informs us, weather the cell employs WPA or WPA2. If not, we should look for another cell. You can use wicd to display available connections, it provides neat overview as I wrote above.

From above output, we can gather the ESSID is MYWIFI. Lets assume, the pass-phrase is Mypassphrase1. Please note, that WPA pass-phrase should have at least 8 characters. Now, we will create simple configuration, which is suitable for most instances (friend's home, cafeteria, backpacker or holiday park). We will issue following command:

```
 wpa_passphrase MYWIFI Passphrase1

```

This should appear on the screen:

```
network={
	ssid="MYWIFI"
	#psk="Passphrase1"
	psk=215e6345254e314b3188186742a93c87818dbebf214cb1b3ddb623910cdbec38
}

```

The wpa_passphrase tool simply generates the key in appropriate format, which can be used as a configuration file. We can output it straight away like this:

```
wpa_passphrase MYWIFI Passphrase1 > MYWIFI.conf

```

You can use arbitrary name. It is a good idea to store the config files in separate directory, so you can re-use them, if you come back to the place.

This is pretty much all we need to establish the connection.

**Connecting**

We will use wpa_supplicant and invoke it as a daemon, so the association will be persistent. The command is following:

```
wpa_supplicant -B -Dwext -iwlan0 -cMYWIFI.conf
```

Explanation of parameters:

[LIST]
[*]-B makes wpa_supplicant run in the background as a daemon
[*]-Dwext specifies the wext driver. This is appropriate in most instances, wext means generic Linux wireless extensions
[*]-iwlan0 - our Wi-Fi device
[*]-cMYWIFI.conf - our configuration file with parsed passphrase
[/LIST]

After this, we can request IP address:

```
dhclient wlan0

```
Once you get the IP address, you are ready to browse the internet.


**Wrapping it up**

This is the bare minimum you need to do in order to connect on demand, assuming we are changing locations frequently. You can wrap up the steps to a script, if you do not want to remember all commands. There are numerous ways of doing that, but follow the KISS rule - Keep It Simple Stupid ;-). If you choose to remember how to generate simple config file, you can wrap the connecting step in this fashion:

```
#!/bin/bash
#Your interface should be specified here, makes it easier as we would need it twice.
INTERFACE=wlan0

#Check for privileges, we need to be root or use sudo 
if test `whoami` != root
then
echo "Must be root. Use \"sudo `basename $0`.\""
exit
fi


#Testing parameters. If run without one, also provides little help how to generate the config file.
#You can use arbitrary name for config_file, the most practical would be location_name.conf.
#Also, take a notice, where the file would be stored
if test $# -lt 1
then
cat << EOF
Need config file as a parameter!
Usage: "`basename $0` config_file"
To generate config file, run "wpa_passphrase ESSID PASSPHRAZE > config_file".
EOF
exit
fi

wpa_supplicant -B -Dwext -i$INTERFACE -c"$1"

dhclient $INTERFACE

```

Store the above code in the file named myconnect, and make it executable:

```
chmod 755 myconnect
```

In order to connect, run it like this:

```
sudo ./myconnect config_file
```

If you store it in your path (for example in /usr/local/bin), you can ommit ./ in front of the file name.

---

