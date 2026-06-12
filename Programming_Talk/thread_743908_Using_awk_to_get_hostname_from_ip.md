---
title: "Using awk to get hostname from ip"
date: 2008-04-03
forum: Programming Talk
---

### Post by Bunghi on 2008-04-03
Hi guys. 

This is my second post in this great forum. I'm not an advanced linux user but I'm trying to resolve all the problems for myself. 

I'm in a situation that I can't do more.. well.. there we go. I'm using Ubuntu 7.10 i386 Server edition because I want to use Hylafax as my fax server. All works fine but there are no reports about hylafax facsimiles, just a log file, the xferfaxlog file located in /var/spool/hylafax/log directory.  

This is a xferfaxlog file: 
```
03/30/08 03:09	SEND	000000007	ttyS0	1	""	anonymous@localhost	"935872980"	""	2211880	0	0:09	0:00	"No local dialtone"	""	""	""	"anonymous"	"00 00 00"
03/30/08 03:14	SEND	000000008	ttyS0	1	""	anonymous@localhost	"935872980"	""	2211880	0	1:06	0:00	"Unknown problem"	""	""	""	"anonymous"	"00 00 00"
03/30/08 03:35	SEND	000000009	ttyS0	4	""	anonymous@localhost	"0935872980"	"935872980"	3407912	0	0:18	0:04	""	""	""	""	"anonymous"	"00 00 00"
03/30/08 03:38	SEND	000000010	ttyS0	5	""	cba@192.168.0.118	"0935872980"	"935872980"	3416105	1	0:57	0:42	""	""	""	""	"cba"	"00 00 00"
```

I use this simple awk script to generate an html file from this log file:
```
BEGIN { 
	FS = "\t"
	print "<!DOCTYPE html PUBLIC \"-//W3C//DTD XHTML 1.0 Strict//EN\""
    	print "\"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd\">"
	print "<html xmlns=\"http://www.w3.org/1999/xhtml\">"
	print "<head><title>Informe</title>"
	print "<style type=\"text/css\">"
	print "table td { text-align: center; }"
	print "</style>"
	print "</head>"
	print "<body>"
	print "<h1 ALIGN=CENTER> INFORMES DE HYLAFAX </h1>"
	print "<br> </br>"
	print "<table width=\"100%\" border=\"1\">"
	print "<tr>"
	print "<td> <b>Fecha y Hora<!-- 1 --></b></td>"
        print "<td> <b>Tipo <!-- 2 --></b</td>"
        print "<td> <b>Job ID <!-- 5 --></b</td>"
        print "<td> <b>Remitente/Fax <!-- 7 --></b</td>"
        print "<td> <b>Destino/Local <!-- 8 --></b</td>"
        print "<td> <b>Paginas <!-- 11 --></b</td>"
        print "<td> <b>Error <!-- 14 --></b</td>"
 	print "</tr>"
 }

{ print "<tr><td>" $1 "</td>", "<td>" $2 "</td>", "<td>" $5 "</td>", "<td>" $7 "</td>", "<td>" $8 "</td>", "<td>" $11 "</td>", "<td>" $14  "</td></tr>" }

END { print "</table></body></html>" }
```

.. and the html file was generated (attached file)
I'm using this script to get it work in the easier way (for me :):
```
#!/bin/bash          
 awk -f /etc/init.d/hylafaxlog/organiza.awt /var/spool/hylafax/log/xferfaxlog > /var/www/index.html
```

Well, now I want to convert the 4th column format in that way to show only the hostname, not the ip address. Ex: cba@192.168.0.118 -> cba@hostname

Sorry for my english. I hope somebody can help me. Thanks for all!

---

### Post by ghostdog74 on 2008-04-03
> **Bunghi said:**
> 
Well, now I want to convert the 4th column format in that way to show only the hostname, not the ip address. Ex: cba@192.168.0.118 -> cba@hostname

i suppose 192.168.0.118 is the machine where you run your script? 
you can use nslookup to find the hostname.
snippet, assume that_ip is already parsed from the respective field.
```

awk 'BEGIN {
 cmd="nslookup  " that_ip
 while  (( cmd | getline  line) > 0 ) {
  if ( line ~ /name =/ ) {
   gsub(".*name = " , "",line)
   hostname=line
   print hostname
  }
 } 
}
'

```
or if you have already defined the host file, you can use the "hostname" command instead

---

### Post by Bunghi on 2008-04-03
Hi and thanks for your support. 

The script is on the fax server and there could be more than one IP. I want to modifty the awk script by adding some line to convert the $7 field and return the sender IP (this can be whatever IP on the lan). 

I wish you got my idea. 

OMG, this is the fastest forum on the web :))

---

### Post by ghostdog74 on 2008-04-03
> **Bunghi said:**
> Hi and thanks for your support. 

The script is on the fax server and there could be more than one IP. I want to modifty the awk script by adding some line to convert the $7 field and return the sender IP (this can be whatever IP on the lan). 

I wish you got my idea. 

OMG, this is the fastest forum on the web :))

if you have more than one IP, store them in awk arrays.
eg
```

h[that_ip]=hostname

```

---

### Post by Bunghi on 2008-04-03
Hi again.

Thanks for helping me. I was thinking that if I have the username without @ip is enought. Now, how can I remove @ip from this string "user@ip"? In the awk script this is $4.

;)

---

### Post by ghostdog74 on 2008-04-03
> **Bunghi said:**
> Hi again.

Thanks for helping me. I was thinking that if I have the username without @ip is enought. Now, how can I remove @ip from this string "user@ip"? In the awk script this is $4.

;)
some ways, using sub or gsub
```

gsub(/@.*/, "",$4)

```
or split
```

split($4,a,"@")

```
a[1] will be user

---

