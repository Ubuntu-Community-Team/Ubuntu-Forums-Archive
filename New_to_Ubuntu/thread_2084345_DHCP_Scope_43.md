---
title: "DHCP Scope 43"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by ubnewb5 on 2012-11-15
I have setup a dhcp server using ubuntu 11.04 and this is issuing IP addresses correctly.  I'm need to add in a DHCP scope optiond 43 which on windows is vendor specific info but cant seem to get this to work.
 
I have Trapeze wireless Access Points and need the option 43 to point them to the wireless controller which is held on seperate network.  Is this possible or is there another way i can achieve this?

---

### Post by Lars Noodén on 2012-11-15
Which DHCP server are you using, dnsmasq or isc-dhcp-server?

---

### Post by ubnewb5 on 2012-11-15
I'm using isc-dhcp-server

---

### Post by davebb on 2013-02-15
This took a lot of work between a coworker and I to make this marriage work because we had it working before, but we wanted DHCP to also handle netbios control. We disabled netbios via DHCP.  
with isc-dhcp within the /etc/dhcp/dhcpd.conf file

###############################
set vendor-id = option vendor-class-identifier;

option netbios code 180 = string;

option space MSFT;
option MSFT.disable-netbios-over-tcpip code 1 = unsigned integer 32;
option MSFT.release-dhcp-lease-on-shutdown code 2 = unsigned integer 32;

class "MSFT 5.0" {
        match if option vendor-class-identifier = "MSFT 5.0";
        option vendor-class-identifier "MSFT 5.0";
        if config-option netbios = "off" {
                vendor-option-space MSFT;
                option MSFT.disable-netbios-over-tcpip 2;
                option MSFT.release-dhcp-lease-on-shutdown 1;
                } else {
                vendor-option-space MSFT;
                option MSFT.disable-netbios-over-tcpip 1;
                option MSFT.release-dhcp-lease-on-shutdown 1;
                }
        }
class "MSFT 98" {
        match if option vendor-class-identifier = "MSFT 98";
        option vendor-class-identifier "MSFT 98";
        if config-option netbios = "off" {
                vendor-option-space MSFT;
                option MSFT.disable-netbios-over-tcpip 2;
                option MSFT.release-dhcp-lease-on-shutdown 1;
                } else {
                vendor-option-space MSFT;
                option MSFT.disable-netbios-over-tcpip 1;
                option MSFT.release-dhcp-lease-on-shutdown 1;
                }
        }
class "WIRELESS-AP:MP_522" {
        match if option vendor-class-identifier = "WIRELESS-AP:MP_522";
        option vendor-class-identifier "WIRELESS-AP:MP_522";
        option vendor-encapsulated-options "ip: 10.x.y.11,10.x.y.12";
        }
class "WIRELESS-AP:MP_432" {
        match if option vendor-class-identifier = "WIRELESS-AP:MP_432";
        option vendor-class-identifier "WIRELESS-AP:MP_432";
        option vendor-encapsulated-options "ip: 10.x.y.11,10.x.y.12";
        }
class "WIRELESS-AP:2332-A1" {
        match if option vendor-class-identifier = "WIRELESS-AP:2332-A1";
        option vendor-class-identifier "WIRELESS-AP:2332-A1";
        option vendor-encapsulated-options "ip: 10.x.y.11,10.x.y.12";
        }

## This was originally used BEFORE attempting the netbios control which is 
## also option 43
#option wss-id code 43 = string;
#option wss-id "ip: 10.8.12.11,10.8.12.12";
#################################
Hope this helps, this was created with many days of searching both microsoft and trapeze and isc based forums.

---

