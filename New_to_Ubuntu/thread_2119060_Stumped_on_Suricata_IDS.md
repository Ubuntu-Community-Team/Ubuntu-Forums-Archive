---
title: "Stumped on Suricata IDS"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by Roskow on 2013-02-22
I realize there are quite a few Sticky write ups in the security section. I'm posting this because I've trying to run the Suricata IDS/IPS and running into a strange error. 

Because I'm a noob, I followed this Package based install. This part went fine. 
[https://redmine.openinfosecfoundation.org/projects/suricata/wiki/Ubuntu_Installation_-_Personal_Package_Archives_(PPA](https://redmine.openinfosecfoundation.org/projects/suricata/wiki/Ubuntu_Installation_-_Personal_Package_Archives_(PPA))

The installer included the Oinkmaster.conf file which I edited to add Rules files with my free OinkCode. This step when fine as well. 

[https://redmine.openinfosecfoundation.org/projects/suricata/wiki/Rule_Management_with_Oinkmaster](https://redmine.openinfosecfoundation.org/projects/suricata/wiki/Rule_Management_with_Oinkmaster)

I then changed the /etc/default/suricata file to Run=Yes.  Rebooted and I see it add more logs under /Var/Logs/.

Suricata then seems to be running as a Process. Although there are other CLI directions to run it.  

$suricata /etc/suricata/suricata-debian.yaml -i eth0

[https://redmine.openinfosecfoundation.org/projects/suricata/wiki/Command_Line_Options](https://redmine.openinfosecfoundation.org/projects/suricata/wiki/Command_Line_Options)

The directions in the last link are where I have problems. Based on that I try $suricata /etc/suricata/suricata-debian.yaml -i eth0. I see it try to load and then end with an Engine Failure. Google it and this is typically a failure of entering the wrong -i interface option. My interface is eth0 so I don't understand the cause of the problem. 

It's not clear to me if this program is running or how I should run it.  

I have tried a Backtrack tool called PytBull to test Suricata and it seems to 100% fail. I also don't see PytBull triggering anything in the logs. 

So after that vent, I'm wondering if I'm in over my head. I should probably be using something more established with clear documentation. I've avoided Snort because all tutorials I look at say I need 2 NICs. 

Could a noobie do better trying Ossec?

EDIT:  I dumped Suricata.  I have Ossec running.  I don't know what the hell went wrong with Suricata.

---

