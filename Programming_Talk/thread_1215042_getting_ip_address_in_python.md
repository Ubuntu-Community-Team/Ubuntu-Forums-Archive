---
title: "getting ip address in python"
date: 2009-07-16
forum: Programming Talk
---

### Post by lavinog on 2009-07-16
I was looking into ways of getting the ip address of a local network device using python.
so far I found the following ways:
```

#!/bin/env python
'''
Different ways to get the ip address of a network device
'''


def get_ip_address_1(ifname='eth0'):
    '''
    Source:
    http://code.activestate.com/recipes/439094/
    '''
    import socket
    import fcntl
    import struct

    s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    ipaddr = socket.inet_ntoa(fcntl.ioctl(
        s.fileno(),
        0x8915,  # SIOCGIFADDR
        struct.pack('256s', ifname[:15])
    )[20:24])
    
    return ipaddr

def get_ip_address_2():
    '''
    Source:
    http://commandline.org.uk/python/how-to-find-out-ip-address-in-python/
    '''
    import socket
    s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    s.connect(('google.com', 0))
    ipaddr=s.getsockname()[0]
    return ipaddr

def get_ip_address_3():
    import socket
    ipaddr = socket.gethostbyname(socket.gethostname())
    return ipaddr

def get_ip_address_4(netdev='eth0'):
    # Use ip addr show
    import subprocess
    arg='ip addr show ' + netdev    
    p=subprocess.Popen(arg,shell=True,stdout=subprocess.PIPE)
    data = p.communicate()
    sdata = data[0].split('\n')
    macaddr = sdata[1].strip().split(' ')[1]
    ipaddr = sdata[2].strip().split(' ')[1].split('/')[0]
    return (ipaddr,macaddr)
    
def get_ip_address_5():
    #Use ip route list
    import subprocess
    arg='ip route list'    
    p=subprocess.Popen(arg,shell=True,stdout=subprocess.PIPE)
    data = p.communicate()
    sdata = data[0].split()
    ipaddr = sdata[ sdata.index('src')+1 ]
    netdev = sdata[ sdata.index('dev')+1 ]
    return (ipaddr,netdev)
    
print(get_ip_address_1())
print(get_ip_address_2())
print(get_ip_address_3())
print(get_ip_address_4())
print(get_ip_address_5())


```

#2 looks like it requires internet access
#3 doesn't work on my system, it just reports 127.0.0.1

#4 & 5 use the ip command in bash, and I don't know how consistent the results would be between machines.

I thought about parsing the output of ifconfig, but it looks like the ip commands give better output

I noticed that I can get the ipv6 address from /proc/net/if_inet6 , but nothing in /proc seems to have the ipv4 address.

I can use these functions for what I am working on, but I was curious if there are better methods?

---

### Post by tqx on 2009-07-16
> **lavinog said:**
> 
#4 & 5 use the ip command in bash, and I don't know how consistent the results would be between machines.


It's not consistent, and it's also not cross-platform.

---

### Post by lavinog on 2009-07-17
> **tqx said:**
> It's not consistent, and it's also not cross-platform.

how about now?
[php]
def get_ip_address():
    import socket
    # 1: Use the gethostname method

    ipaddr = socket.gethostbyname(socket.gethostname())
    if not( ipaddr.startswith('127') ) :
        print('Can use Method 1: ' + ipaddr)
        #return ipaddr

    # 2: Use outside connection
    '''
    Source:
    http://commandline.org.uk/python/how-to-find-out-ip-address-in-python/
    '''

    ipaddr=''
    s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    try:
        s.connect(('google.com', 0))
        ipaddr=s.getsockname()[0]
        print('Can used Method 2: ' + ipaddr)
        #return ipaddr
    except:
        pass


    # 3: Use OS specific command
    import subprocess , platform
    ipaddr=''
    os_str=platform.system().upper()

    if os_str=='LINUX' :

        # Linux:
        arg='ip route list'    
        p=subprocess.Popen(arg,shell=True,stdout=subprocess.PIPE)
        data = p.communicate()
        sdata = data[0].split()
        ipaddr = sdata[ sdata.index('src')+1 ]
        #netdev = sdata[ sdata.index('dev')+1 ]
        print('Can used Method 3: ' + ipaddr)
        #return ipaddr

    elif os_str=='WINDOWS' :

        # Windows:
        arg='route print 0.0.0.0'    
        p=subprocess.Popen(arg,shell=True,stdout=subprocess.PIPE)
        data = p.communicate()
        strdata=data[0].decode()
        sdata = strdata.split()

        while len(sdata)>0:
            if sdata.pop(0)=='Netmask' :
                if sdata[0]=='Gateway' and sdata[1]=='Interface' :
                    ipaddr=sdata[6]
                    break
        print('Can used Method 4: ' + ipaddr)
        #return ipaddr


get_ip_address()
[/php]

I don't have a mac available to me.

---

