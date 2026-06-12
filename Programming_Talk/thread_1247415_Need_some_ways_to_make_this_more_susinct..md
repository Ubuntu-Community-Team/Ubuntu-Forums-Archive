---
title: "Need some ways to make this more susinct."
date: 2009-08-22
forum: Programming Talk
---

### Post by _UsUrPeR_ on 2009-08-22
Hey all.

I have "finished" this quick script to create a globalconfig.xml out of a server's dhcpd.conf list for italc, and I KNOW that I have not done this properly. I mean, it works, but I would like to get some hints about shortening this up.

To be specific, I am sure that there's a better way to create and assign arrays than I have done in Findfile(). Inspect() is also the same way. The reason Inspect is there is to ensure that the file entered is a valid dhcpd.conf.

Thanks in advance.

```
#!/bin/bash


Pause()
{
        key=""
	echo
        echo "This will create an italc globalconfig.xml"
	echo "in the directory where this program has been run."
	echo -n "Press any key to continue..."
        stty -icanon
       	key=`dd count=1 2>/dev/null`
        stty icanon
}


Locate()
{
	Location=""

	echo
	echo -n "The location of your ltsp dhcpd.conf [/etc/ltsp/dhcpd.conf]:"
	read Location

	if [[ $Location = "" ]]
		then
		Location="/etc/ltsp/dhcpd.conf"
	fi
}


FindFile()
{
	if [[ ! -e "$Location" ]]
	then
		echo "File not found!"
		exit 1
	fi

	cat $Location |grep fixed-address|cut -d " " -f2|cut -d ";" -f1 > /tmp/cat_ip
	cat $Location |grep "hardware ethernet"|cut -d " " -f3|cut -d ";" -f1 > /tmp/cat_mac
}


Inspect()
{
	RETURN=`ls -alh /tmp/cat_ip |cut -d " " -f5`

	if [[ $RETURN == "0" ]]
	then
		echo "Sorry, that was not a proper dhcpd.conf"
                rm /tmp/cat_ip
		exit 1
	else
	Enumerate
	fi
}


Enumerate()
{
	i=1
	while [[ `sed -n "$i{p;q;}" /tmp/cat_ip` != "" ]] 
	do
		ip_array[$i]=`sed -n "$i{p;q;}" /tmp/cat_ip`
		mac_array[$i]=`sed -n "$i{p;q;}" /tmp/cat_mac`
		let "i=$i+1"
	done
}


Create()
{
	o=1
	count=`wc -l /tmp/cat_ip|cut -d " " -f1`

	echo '<?xml version="1.0"?>' > ./globalconfig.xml
	echo '<!DOCTYPE italc-config-file>' >>./globalconfig.xml
	echo '<globalclientconfig version="1.0.9" >' >>./globalconfig.xml
	echo '  <body>' >>./globalconfig.xml
	echo '   <classroom name="SchoolTech Classroom" >' >>./globalconfig.xml

		while [[ $o -le $count ]]
		do
			echo '    <client hostname"'${ip_array[$o]}'" mac="'${mac_array[$o]}'" type="0" id="'$o'" name="client'$o'" />' >>./globalconfig.xml
			let "o=$o+1"
		done

	echo '    </classroom>' >>./globalconfig.xml
	echo '  </body>' >>./globalconfig.xml
	echo '</globalclientconfig>' >>./globalconfig.xml
	rm /tmp/cat_ip
	rm /tmp/cat_mac
}

Pause
Locate
FindFile
Inspect
Create

echo
echo "Your file is complete."
exit 1
```

---

### Post by nvteighen on 2009-08-23
Well, try to separate user interface from implementation. I mean, all those echos are placed in the middle of the program's processing tasks... and that's quite a bad way to do this.

The best is to create separate functions that do the user interface stuff... and connect them with the implementation through useful return values. So, if some function returns 789, you know the message to show is "whatever".

---

### Post by geirha on 2009-08-23
**Pause()**
```
read -n1 -p "Press any key to continue..."
help read   # For help on the builtin read command

```

**Locate()**
You may find bash's read's -e option of value. Also, with parameter expansion, you can do away with that if-block.
```
Location=${Location:-/etc/ltsp/dhcpd.conf}
# or
: "${Location:=/etc/ltsp/dhcpd.conf}"

```
[http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)

**FindFile()**
Ok, several points here. 

1. Learn to quote. The one place where you didn't need to quote parameter expansions here, you did quote - inside the [[-keyword (It doesn't hurt to quote it though). With the cat-command: «cat $Location», the expansion is subject to word splitting and glob expansion, so make sure you quote it - «cat "$Location"».
[http://bash-hackers.org/wiki/doku.php/syntax/words](http://bash-hackers.org/wiki/doku.php/syntax/words)
[http://www.grymoire.com/Unix/Quote.html](http://www.grymoire.com/Unix/Quote.html)

2. «cat file | grep pattern» is useless use of cat. Just pass the file as an argument to grep instead - «grep pattern file»

3. Don't use temporary files with static names. Imagine the mess if this script is run more than once, simultaniously. Use mktemp to create files with random names instead
```
tempfile=$(mktemp)
echo "something" >> "$tempfile"

man mktemp

```

4. Personally, I'd use bash, rather than grep and cut, to parse that.
```

ip_array=() mac_array=()
while read line; do
    case $line in
        fixed-address*) 
            IFS='; ' read _ value <<< "$line"
            ip_array+=( "$value" )
        ;;
        "hardware ethernet"*)
            IFS='; ' read _ _ value <<< "$line"
            mac_array+=( "$value" )
        ;;
    esac
done < "$Location"

```
[http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001)

**Inspect()**
```
help test | grep -- -s
```

**Enumerate()**

```

ip_array=( $(</tmp/cat_ip) )
mac_array=( $(</tmp/cat_mac) )

```
Unless you use the while read I suggested earlier.

**Create()**

1. Write to a temporary file first, then rename it to the correct name at the very end. That should ensure that you don't end up with a half-finished file if the script is interupted.

2. To avoid redirecting almost every line of that function, you can group the commands together with { ;}
```

{ 
  echo "line 1"
  echo "line 2"
} > some_file

```
Or you could simply remove all the redirections inside the function, then redirect the whole function instead. «Create > some_file»

3. To loop through an array by its indices:
```
n=${#ip_array[@]}   #number of elements in ip_array
for ((i=0; i<n; i++)); do
  echo "${ip_array[i]}, ${mac_array[i]}"
done

```

---

