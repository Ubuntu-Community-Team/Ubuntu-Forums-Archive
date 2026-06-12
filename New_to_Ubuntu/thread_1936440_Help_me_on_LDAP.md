---
title: "Help me on LDAP"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by phani247 on 2012-03-06
Hi every one iam using ubuntu 10.04 LTS
recently i shifted to ubuntu from windows 
in my ofc we are planning to build ubuntu server for that iam configuring ubuntu 10.04

i succesfully installed 
DNS
DHCP
NIS
and
NFS

but i dont know abt LDAP but by following some tutorials i configure LDAP..
but iam getting error 
following is the command and o/p plz help me

[INDENT]root@vedicind:~#[COLOR=Red] ldapsearch -D "cn=admin,dc=dcvsplhyd,dc=com" -W -d 255
[/COLOR][/INDENT]ldap_create
Enter LDAP Password: 
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP localhost:389
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 127.0.0.1:389
ldap_pvt_connect: fd: 3 tm: -1 async: 0
ldap_open_defconn: successful
ldap_send_server_request
ber_scanf fmt ({it) ber:
ber_dump: buf=0x217d9d18 ptr=0x217d9d18 end=0x217d9d4c len=52
  0000:  30 32 02 01 01 60 2d 02  01 03 04 1c 63 6e 3d 61   02...`-.....cn=a  
  0010:  64 6d 69 6e 2c 64 63 3d  64 63 76 73 70 6c 68 79   dmin,dc=dcvsplhy  
  0020:  64 2c 64 63 3d 63 6f 6d  80 0a 53 72 69 73 79 73   d,dc=com..Srisys  
  0030:  40 31 32 33                                        @123              
ber_scanf fmt ({i) ber:
ber_dump: buf=0x217d9d18 ptr=0x217d9d1d end=0x217d9d4c len=47
  0000:  60 2d 02 01 03 04 1c 63  6e 3d 61 64 6d 69 6e 2c   `-.....cn=admin,  
  0010:  64 63 3d 64 63 76 73 70  6c 68 79 64 2c 64 63 3d   dc=dcvsplhyd,dc=  
  0020:  63 6f 6d 80 0a 53 72 69  73 79 73 40 31 32 33      com..Srisys@123   
ber_flush2: 52 bytes to sd 3
  0000:  30 32 02 01 01 60 2d 02  01 03 04 1c 63 6e 3d 61   02...`-.....cn=a  
  0010:  64 6d 69 6e 2c 64 63 3d  64 63 76 73 70 6c 68 79   dmin,dc=dcvsplhy  
  0020:  64 2c 64 63 3d 63 6f 6d  80 0a 53 72 69 73 79 73   d,dc=com..Srisys  
  0030:  40 31 32 33                                        @123              
ldap_write: want=52, written=52
  0000:  30 32 02 01 01 60 2d 02  01 03 04 1c 63 6e 3d 61   02...`-.....cn=a  
  0010:  64 6d 69 6e 2c 64 63 3d  64 63 76 73 70 6c 68 79   dmin,dc=dcvsplhy  
  0020:  64 2c 64 63 3d 63 6f 6d  80 0a 53 72 69 73 79 73   d,dc=com..Srisys  
  0030:  40 31 32 33                                        @123              
ldap_result ld 0x217d10d8 msgid 1
wait4msg ld 0x217d10d8 msgid 1 (infinite timeout)
wait4msg continue ld 0x217d10d8 msgid 1 all 1
** ld 0x217d10d8 Connections:
* host: localhost  port: 389  (default)
  refcnt: 2  status: Connected
  last used: Tue Mar  6 13:47:02 2012


** ld 0x217d10d8 Outstanding Requests:
 * msgid 1,  origid 1, status InProgress
   outstanding referrals 0, parent count 0
  ld 0x217d10d8 request count 1 (abandoned 0)
** ld 0x217d10d8 Response Queue:
   Empty
  ld 0x217d10d8 response count 0
ldap_chkResponseList ld 0x217d10d8 msgid 1 all 1
ldap_chkResponseList returns ld 0x217d10d8 NULL
ldap_int_select
read1msg: ld 0x217d10d8 msgid 1 all 1
ber_get_next
ldap_read: want=8, got=8
  0000:  30 0c 02 01 01 61 07 0a                            0....a..          
ldap_read: want=6, got=6
  0000:  01 31 04 00 04 00                                  .1....            
ber_get_next: tag 0x30 len 12 contents:
ber_dump: buf=0x217dadb8 ptr=0x217dadb8 end=0x217dadc4 len=12
  0000:  02 01 01 61 07 0a 01 31  04 00 04 00               ...a...1....      
read1msg: ld 0x217d10d8 msgid 1 message type bind
ber_scanf fmt ({eAA) ber:
ber_dump: buf=0x217dadb8 ptr=0x217dadbb end=0x217dadc4 len=9
  0000:  61 07 0a 01 31 04 00 04  00                        a...1....         
read1msg: ld 0x217d10d8 0 new referrals
read1msg:  mark request completed, ld 0x217d10d8 msgid 1
request done: ld 0x217d10d8 msgid 1
res_errno: 49, res_error: <>, res_matched: <>
ldap_free_request (origid 1, msgid 1)
ldap_parse_result
ber_scanf fmt ({iAA) ber:
ber_dump: buf=0x217dadb8 ptr=0x217dadbb end=0x217dadc4 len=9
  0000:  61 07 0a 01 31 04 00 04  00                        a...1....         
ber_scanf fmt (}) ber:
ber_dump: buf=0x217dadb8 ptr=0x217dadc4 end=0x217dadc4 len=0

ldap_msgfree
ldap_err2string
ldap_bind: Invalid credentials (49)

---

### Post by Gone fishing on 2012-03-06
This looks like what you might need.

[http://ubuntuforums.org/showthread.php?t=1515119](http://ubuntuforums.org/showthread.php?t=1515119)

---

