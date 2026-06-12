---
title: "Need support for getting snmwalk output in excel"
date: 2015-05-26
forum: Programming Talk
---

### Post by Hitesh_Kumar on 2015-05-26
Hello Guys 


I am a newbie in linux and getting a issue in creating a new script in which i need to export my snmp walk output in excel file with name change as "CPU Utlisation is 72".


below mentioned is the script for reference and snmp walk output.
while true ; do
        
echo -n `date --rfc-3339=seconds`","
 
        snmpget -v2c -Cf -c public 172.16.13.10 .1.3.6.1.4.1.2636.3.39.1.12.1.1.1.5.0
    
    sleep 10




 awk '{if (Gauge32: >0) print $17}' OFS="," > /home/administrator/Documents/sample.xls
 
done




Br
Hitesh

---

