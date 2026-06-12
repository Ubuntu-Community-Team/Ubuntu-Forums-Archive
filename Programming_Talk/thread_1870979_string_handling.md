---
title: "string handling"
date: 2011-10-28
forum: Programming Talk
---

### Post by jpjohnj on 2011-10-28
i need to get the mac address for interface...

( with only using "sed")


actually i got this ...


ip link show dev eth2|sed '$!d'


and the out put was ...


link/ether 00:12:0e:00:00:00 brd ff:Ff:Ff:ff:ff:Ff


in above i only need "00:12:0e:00:00:00" .   


help me to do that with sed.... ( not with awk,cut,tail,grep)

---

### Post by nothingspecial on 2011-10-28
Hi jpjohnj,

Is this homework?

---

### Post by jpjohnj on 2011-10-28
not home work ..  i need to use that in my program, my device kernel does not support gerp ,cut,tail. so that only i need a help..

---

### Post by Lars Noodén on 2011-10-28
Awk should be on your machine.  

```

ip link show dev eth2 | awk '/link\/ether/ { print $2 }'

```

---

### Post by jpjohnj on 2011-10-28
only string handling function it has was sed  ... please help me to do that....


( help with other than awk,cut,grep,tail,head)

---

### Post by Lars Noodén on 2011-10-28
> **jpjohnj said:**
> only string handling function it has was sed  ... please help me to do that....


( help with other than awk,cut,grep,tail,head)

It may not be possible using only sed.   That's why I proposed awk.  

If you can merge the lines into one, it might be possible to then combine several sed actions.  First merge all the lines into one, then erase everything before the mac address, then erase everything after the mac address.

```

ip link show dev eth2 | sed -e 's/foo//;s/^.*ether[ ]*//;s/[ ]*brd.*$//'

```

The part 'foo' is what I haven't figured out.  That should be the part that eliminates the end of line characters.

---

### Post by Lars Noodén on 2011-10-28
Try this:

```

ip link show dev eth2 | sed -e 'N;s/\n//g;s/^.*ether[ ]*//;s/[ ]*brd.*$//'

```

N = read an extra line, so this should work if ip outputs exactly two lines, no more, no less

---

### Post by jpjohnj on 2011-10-28
thank for your help..


could you explain that to me in a clear way... 


sed -e 's/foo//;s/^.*ether[ ]*//;s/[ ]*brd.*$//'

and 


sed -e 'N;s/\n//g;s/^.*ether[ ]*//;s/[ ]*brd.*$//'

---

### Post by Lars Noodén on 2011-10-28
This should work with an arbitrary number of lines but assuming only one has 'ether' in it:

```

ip link show dev eth2 | sed -n '/ether/p'  | sed -e 's/^.*ether[ ]*//;s/[ ]*brd.*$//'

```

---

### Post by Lars Noodén on 2011-10-28
> **jpjohnj said:**
> thank for your help..


could you explain that to me in a clear way... 


sed -e 's/foo//;s/^.*ether[ ]*//;s/[ ]*brd.*$//'

and 


sed -e 'N;s/\n//g;s/^.*ether[ ]*//;s/[ ]*brd.*$//'

You have multiple substitutions, each one is s///

The first part is the regex you find, the second is what your replace, s/find/replace/

[] means find any characters that match the ones between the brackets, in this case as space

* means match zero or more characters, when combined with the brackets containing a space, it means match zero or more spaces

ether and brd are the strings ether and brd

^ means start matching from the beginning of the line
$ means match until the very end of the line

Normally sed only matches one line at at time, but N means read in an extra line first.


Does that help?

[http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)

---

### Post by jpjohnj on 2011-10-28
thank you...

---

### Post by mörgæs on 2011-10-28
Moved to Programming Talk.

If the problem is solved, please mark the thread so using 'thread tools'.

---

### Post by Lars Noodén on 2011-10-28
And one last one for the archive. 
```

ip link show dev eth2 | \
sed [':a;N;$!ba;s/\n//g'](http://linux.dsplabs.com.au/rmnl-remove-new-line-characters-tr-awk-perl-sed-c-cpp-bash-python-xargs-ghc-ghci-haskell-sam-ssam-p65/) | \
sed -e 's/^.*ether[ \t]*//;s/[ \t]*brd.*$//' 

```
I hope I can find it easily next time I need it.  :)

---

