---
title: "sed question - dhcpd.conf"
date: 2007-10-29
forum: Programming Talk
---

### Post by mnarinsky on 2007-10-29
Hi!!

I'm trying to comment out a block of specific subnet from dhcpd.conf file

e.g.

Input:
```
subnet 10.10.10.0 netmask 255.255.255.0 {
	host host1{
		ddns-hostname "host1";
		hardware ethernet 00:11:22:33:44:55;
		fixed-address 192.168.7.113;
	}

	host host2{
		ddns-hostname "host2";
		hardware ethernet 00:11:22:33:44:55;
		fixed-address 192.168.7.113;
	}

	host host3{
		ddns-hostname "host3";
		hardware ethernet 00:11:22:33:44:55;
		fixed-address 192.168.7.113;
		}
	}

subnet 10.10.11.0 netmask 255.255.255.0 {
	host host4{
			ddns-hostname "host4";
			hardware ethernet 00:11:22:33:44:55;
			fixed-address 192.168.7.113;
	}
}

subnet 10.10.10.0 netmask 255.255.255.0 {
	host host5{
		ddns-hostname "host5";
		hardware ethernet 00:11:22:33:44:55;
		fixed-address 192.168.7.113;
	}
}

```

Output:
```


#subnet 10.10.10.0 netmask 255.255.255.0 {
#	host host1{
#		ddns-hostname "host1";
#		hardware ethernet 00:11:22:33:44:55;
#		fixed-address 192.168.7.113;
#	}
#
#	host host2{
#		ddns-hostname "host2";
#		hardware ethernet 00:11:22:33:44:55;
#		fixed-address 192.168.7.113;
#	}
#
#	host host3{
#		ddns-hostname "host3";
#		hardware ethernet 00:11:22:33:44:55;
#		fixed-address 192.168.7.113;
#		}
#	}


subnet 10.10.11.0 netmask 255.255.255.0 {
	host host4{
			ddns-hostname "host4";
			hardware ethernet 00:11:22:33:44:55;
			fixed-address 192.168.7.113;
	}
}

#subnet 10.10.10.0 netmask 255.255.255.0 {
#	host host5{
#		ddns-hostname "host5";
#		hardware ethernet 00:11:22:33:44:55;
#		fixed-address 192.168.7.113;
#	}
#}


```

I'm trying this command:

	[B]cat /etc/dhcp.conf | paste -sd\| | \
	sed -e 's/\(subnet\s*10.10.10.0[^{]*{.*}.*\)\((subnet|.*\)/comment_block_start\n\1\ncomment_block_end\n\2/g' \
	-e 'y/|/\n/' | \
	sed -e '/comment_block_start/,/comment_block_end/s/^/#/' [/B]

but it doesn't work very well for me.

Does anyone have better ideas??

Thanks a lot!!

---

### Post by ghostdog74 on 2007-10-29
```

awk '/subnet 10.10.10.0/{f=1;print"#"$0;next}
    /^subnet/ && !/10.10.10.0/ {f=0}
    f{print "#"$0}
    f==0{print}    
' "file"

```
output:
```

# ./test.sh
#subnet 10.10.10.0 netmask 255.255.255.0 {
#       host host1{
#               ddns-hostname "host1";
#               hardware ethernet 00:11:22:33:44:55;
#               fixed-address 192.168.7.113;
#       }
#
#       host host2{
#               ddns-hostname "host2";
#               hardware ethernet 00:11:22:33:44:55;
#               fixed-address 192.168.7.113;
#       }
#
#       host host3{
#               ddns-hostname "host3";
#               hardware ethernet 00:11:22:33:44:55;
#               fixed-address 192.168.7.113;
#               }
#       }
#
subnet 10.10.11.0 netmask 255.255.255.0 {
        host host4{
                        ddns-hostname "host4";
                        hardware ethernet 00:11:22:33:44:55;
                        fixed-address 192.168.7.113;
        }
}

#subnet 10.10.10.0 netmask 255.255.255.0 {
#       host host5{
#               ddns-hostname "host5";
#               hardware ethernet 00:11:22:33:44:55;
#               fixed-address 192.168.7.113;
#       }
#}


```

---

### Post by mnarinsky on 2007-10-30
This works!!!!

Thanks!

---

