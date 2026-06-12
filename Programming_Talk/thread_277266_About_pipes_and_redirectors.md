---
title: "About pipes and redirectors"
date: 2006-10-14
forum: Programming Talk
---

### Post by lucifercheff on 2006-10-14
Hello everyone.

I'm making a shell script which use the following command:


cat /etc/dhcp3/dhcpd.conf | grep -v "# wireless" > /etc/dhcp3/dhcpd.conf

That should remove the line containing the chain "# wireless" from the file dhcpd.conf, but let the file emty instead :confused: . The output seems to work well when I run 'cat /etc/dhcp3/dhcpd.conf | grep -v "# wireless"' without redirection.

Somebody knows what's happening?

---

### Post by cwaldbieser on 2006-10-14
> **lucifercheff said:**
> Hello everyone.

I'm making a shell script which use the following command:


cat /etc/dhcp3/dhcpd.conf | grep -v "# wireless" > /etc/dhcp3/dhcpd.conf

That should remove the line containing the chain "# wireless" from the file dhcpd.conf, but let the file emty instead :confused: . The output seems to work well when I run 'cat /etc/dhcp3/dhcpd.conf | grep -v "# wireless"' without redirection.

Somebody knows what's happening?

Not 100% sure, but I believe the redirection operator is being interpreted before the pipeline is executed, so /etc/dhcp3/dhcpd.conf is truncated.

Try something like:
```

$ grep -v "# wireless" /etc/dhcp3/dhcpd.conf > tempfile
$ mv tempfile /etc/dhcp3/dhcpd.conf

```

---

### Post by kidders on 2006-10-14
Hi there,

Are you running into permissions-related problems perhaps?

I'm not altogether sure about the wisdom of doing **cat dhcp.conf > dhcp.conf**. Perhaps you might give this a go:

**cat /etc/dhcp3/dhcpd.conf | grep -v "^# wireless" > /tmp/dhcpd.conf && mv /tmp/dhcpd.conf /etc/dhcp3/dhcpd.conf**

The "&&" means the move will only happen if the first command worked perfectly. In addition, including the "^" in the grep pattern ensures that only lines that *begin* with "# wireless" will get dropped (a minor distinction).

I wonder if this will fix things for you.

**Edit:** Never mind ... I'm just too slow! Hehe. Cwaldbieser is absolutely right about the execution order of the redirect :-)

---

### Post by lucifercheff on 2006-10-15
thanks  a lot, the problem was it is not possible to use a file as the source at the same time as the target on the same command line: cat dhcp.conf > dhcp.conf; so i made a temporary file and it works.

By the way; someone knows how to insert and remove a whole paragraph into a file in a shell script instead of inserting lines one by one?.

---

### Post by kidders on 2006-10-16
There are a few utilities you can use for this sort of thing, like sed, awk, etc. For instance, say you had a "host" block you wanted to take out...

```

..
..

host stupid {
                ddns-hostname "stupid";
                hardware ethernet 00:11:22:33:44:55;
                fixed-address 192.168.7.113;
}

..
..

```

You could drop it with something like **cat /etc/dhcp/dhcpd.conf | paste -sd\| | sed -e 's/host\s*stupid[^}]*}/# stupid removed/' -e 'y/|/\n/'**, and replace it with a little comment to remind you it's gone.

```

..
..

# stupid removed

..
..

```

Adding things is somewhat more straightforward. You could use **echo -e "\nhost stupid {\n\tddns-hostname \"stupid\";\n ........... \n}\n" >> /etc/dhcp/dhcpd.conf**

Of course, these commands can be a nightmare to figure out, especially where regular expressions are involved :neutral: Here's a more full-blown version of removing a chunk of dhcp.conf...

**cat /etc/dhcp/dhcpd.conf | paste -sd\| | sed -e 's/host\s*stupid[^}]*}/# stupid removed/' -e 'y/|/\n/' > /tmp/dhcp.conf && mv -f /tmp/dhcp.conf /etc/dhcp/dhcp.conf && /etc/init.d/dhcp restart**

So, assuming you can wrap your head around all the quoting, escaping, piping & redirecting (which I find a little demanding sometimes, personally), you can modify your DHCP server config and restart in one foul swoop :-)

I hope you don't mind me persisting a little with the example of adding/removing "host" blocks, but with a little fiddling, it strikes me that you could (relatively) easily create yourself a little script called "addhost" that would use awk to calculate a free IP address & sed to insert it in the right place. Throw it in /usr/local/bin with a partner "delhost", and you'd be in business.

Hope that helps!

---

### Post by Woei on 2006-10-16
Wow, lots of of [Useless use of Cat]("http://sial.org/howto/shell/useless-cat/") awards to hand out. ;)

You needn't use ```
cat somefile | someprog > outfile
``` to get the contents of somefile fed to someprog's standard input, as that will spawn one process too many and will result in the file being read twice for no good reason.

Better is any of the following:```

<input someprog -some -switches >outfile
<input >outfile someprog
someprog <input >outfile 2>/dev/null

```

---

### Post by kidders on 2006-10-16
Hehe good point :-)

---

### Post by Ramses de Norre on 2006-10-17
You can also use sed:
```
 sed -e '/^#/d' /etc/dhcp3/dhcpd.conf > /etc/dhcp3/dhcpd.conf
```

---

### Post by Arndt on 2006-10-18
> **Ramses de Norre said:**
> You can also use sed:
```
 sed -e '/^#/d' /etc/dhcp3/dhcpd.conf > /etc/dhcp3/dhcpd.conf
```

Yes, but you will get the same empty file that way. The shell opens the file for writing and then calls 'sed', which will find an empty file there.

---

### Post by Ramses de Norre on 2006-10-18
Ow.. so the shell interpretes the ">" before the actual command..
I'll think about an other way then=)
(And I thought there was a way to make sed itself write his output to a file but I can't find it nomore.)

---

### Post by Arndt on 2006-10-18
> **Ramses de Norre said:**
> Ow.. so the shell interpretes the ">" before the actual command..
I'll think about an other way then=)
(And I thought there was a way to make sed itself write his output to a file but I can't find it nomore.)

-i, apparently. It's in both "man sed" and "sed -h". Perl has a similar option, for that matter.

-i is not a classical option, so if you plan to run your scripts on some other Unix, like Solaris, think some more about it. Otherwise it should be fine.

---

### Post by hillbilly on 2006-10-18
> **lucifercheff said:**
> Hello everyone.

I'm making a shell script which use the following command:


cat /etc/dhcp3/dhcpd.conf | grep -v "# wireless" > /etc/dhcp3/dhcpd.conf

That should remove the line containing the chain "# wireless" from the file dhcpd.conf, but let the file emty instead :confused: . The output seems to work well when I run 'cat /etc/dhcp3/dhcpd.conf | grep -v "# wireless"' without redirection.

Somebody knows what's happening?


you could use the tee command. What tee does is display the output in the STDOUT as well as redirect it to a file. So one way you could do this would be 

```
cat /etc/dhcp3/dhcpd.conf | grep -v "# wireless" |tee|tee /etc/dhcp3/dhcpd.conf
```

Of course test it before you try it.

---

### Post by Arndt on 2006-10-19
> **hillbilly said:**
> you could use the tee command. What tee does is display the output in the STDOUT as well as redirect it to a file. So one way you could do this would be 

```
cat /etc/dhcp3/dhcpd.conf | grep -v "# wireless" |tee|tee /etc/dhcp3/dhcpd.conf
```

Of course test it before you try it.

Beware. It seems to work for small files, but bigger files will be truncated. The only temporary storage for the command chain is the pipe (the '|' connection between the processes), and pipes have limited buffers.

---

### Post by hillbilly on 2006-10-19
Yes you are right !! The buffer for pipes is limited and bigger files most probably would run into problems.

---

### Post by mnarinsky on 2007-10-26
> **kidders said:**
> There are a few utilities you can use for this sort of thing, like sed, awk, etc. For instance, say you had a "host" block you wanted to take out...

```

..
..

host stupid {
                ddns-hostname "stupid";
                hardware ethernet 00:11:22:33:44:55;
                fixed-address 192.168.7.113;
}

..
..

```

You could drop it with something like **cat /etc/dhcp/dhcpd.conf | paste -sd\| | sed -e 's/host\s*stupid[^}]*}/# stupid removed/' -e 'y/|/\n/'**, and replace it with a little comment to remind you it's gone.

```

..
..

# stupid removed

..
..

```



This works great, but only for one host.

What is the sed command if I want to remove all occurences of "subnet" block?????

e.g.

Input:
```
subnet 10.10.10.0 netmask 255.255.255.0 {
	host stupid {
		ddns-hostname "stupid";
		hardware ethernet 00:11:22:33:44:55;
		fixed-address 192.168.7.113;
	}

	host stupid2 {
		ddns-hostname "stupid";
		hardware ethernet 00:11:22:33:44:55;
		fixed-address 192.168.7.113;
	}

	host stupid3 {
		ddns-hostname "stupid";
		hardware ethernet 00:11:22:33:44:55;
		fixed-address 192.168.7.113;
		}
	}

subnet 10.10.11.0 netmask 255.255.255.0 {
	host stupid {
			ddns-hostname "stupid";
			hardware ethernet 00:11:22:33:44:55;
			fixed-address 192.168.7.113;
	}
}

subnet 10.10.10.0 netmask 255.255.255.0 {
	host stupid {
		ddns-hostname "stupid";
		hardware ethernet 00:11:22:33:44:55;
		fixed-address 192.168.7.113;
	}
}

```

Output:
```


#subnet 10.10.10.0 removed

subnet 10.10.11.0 netmask 255.255.255.0 {
	host stupid {
			ddns-hostname "stupid";
			hardware ethernet 00:11:22:33:44:55;
			fixed-address 192.168.7.113;
	}
}

#subnet 10.10.10.0 removed


```

I'm trying this command:
**cat /etc/dhcpd.conf | paste -sd\| | sed -e 's/subnet\s*10.10.10.0[^{]*{.*}.*\(subnet\)/# subnet 10.10.10.0 removed\n\1/g'  -e 'y/|/\n/'**
but it doesn't work very well for me.
:confused:

Thanks a lot!!

---

### Post by Jacks0n on 2007-10-27
Try

```

sed -i -e 's/# wireless//g' /etc/dhcp3/dhcpd.conf

```

---

