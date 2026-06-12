---
title: "Awk and array issue."
date: 2007-09-20
forum: Programming Talk
---

### Post by JinxAu on 2007-09-20
Gday everyone,

I am fairly new to awk, so hopefully this is a simple newbie issue. 

I am looking for some assistance with arrays in awk. The scenario is, I need to get a list of IP addresses, throw them into an array and eventually do a DNS name lookup on each address (will deal with this as a separate issue). 

Getting stuck trying to make sure I do not end up with duplicate array values. Would like to have a unique value for each array element, as that reduces the amount of DNS lookups the script needs to do.

Sample input:
> Table: Links
Local IP        remote IP       Hysteresis      LinkQuality     lost    total   NLQ     ETX
10.64.32.10     10.64.32.11     0.00    1.00    0       100     1.00    1.00
10.64.0.13      10.64.0.211     0.00    0.95    5       100     0.97    1.09
10.64.0.13      10.64.1.2       0.00    0.68    32      100     0.56    2.64
10.64.0.13      10.64.1.3       0.00    0.98    2       100     1.00    1.02
10.64.32.82     10.64.32.83     0.00    1.00    0       100     1.00    1.00


Script I have so far:
```
cat sample | awk '

# only match records starting with IP addresses
/^[0-9][0-9]*\.[0-9][0-9]*\.[0-9][0-9]*\.[0-9][0-9]*/  { 

# traverse each record and copy ip into host_address array if it does not already exist.
for ( f = 1; f <= NF; ++f) {
   if ( $f ~ /[0-9][0-9]*\.[0-9][0-9]*\.[0-9][0-9]*\.[0-9][0-9]*/ && $f !~ /^255\./ ) {
      if ( ip_address[$f] != $f )
         ip_address[$f] = $f 
   }
}      

# print our array of IP addresses.
for ( hosts in ip_address )
   print "Our IP addresses are:", hosts, ip_address[hosts]
      
}'
```

The output leads to the addresses being listed in the ip_address array, but with a load of duplicates.

Ideally, it would be good if the actual index value of each array is the ip address... later on I will be able to populate it with the hostname as the element (if it exists).

As you can see, my understanding of associative arrays and their operation is still a little limited. Hoping you could point me in the right direction as far as dealing with the index and elements.

Hope that makes some sense.

Cya round
Jinx

---

### Post by ghostdog74 on 2007-09-20
i assume you want only the first field of IP address and that the whole input file structure is just like what you have given
```

awk '/^[0-9]/{ iparray[$1]}
END { 
    for ( ips in iparray ){
        print "IP addresses are ", ips
        cmd = "dig " ips #command to query ips
        system(cmd) # cmd | getline
    }
}
' "file"

```
output:
```

# ./test1.sh
IP addresses are  10.64.32.10
dig 10.64.32.10
IP addresses are  10.64.0.13
dig 10.64.0.13
IP addresses are  10.64.32.82
dig 10.64.32.82

```

---

### Post by JinxAu on 2007-09-20
Gday ghostdog,

Thanks for the reply.

I actually wanted to get all of the addresses from the sample file, but only do one lookup per address (the same address can occur more than once in the same record, or on a different record).

I like the system(cmd) function... I was getting worried that I might have to pipe to dig then back again.

Cya round
Jinx

---

### Post by ghostdog74 on 2007-09-20
> **JinxAu said:**
> 
I actually wanted to get all of the addresses from the sample file
then you can defined another array to store the second field, which is also an ip address.. at the END block, use another for loop to do exactly the same.

---

### Post by JinxAu on 2007-09-20
That makes sense. However, it doesn't prevent the issue of performing a lookup for an address that occurs more than once in the input. For example, 10.64.0.13 occurs more than once in field $1... How would you go about ensuring that only one lookup happens per address?

Cya round
Jinx

---

### Post by ghostdog74 on 2007-09-20
> **JinxAu said:**
> That makes sense. However, it doesn't prevent the issue of performing a lookup for an address that occurs more than once in the input. For example, 10.64.0.13 occurs more than once in field $1... How would you go about ensuring that only one lookup happens per address?

Cya round
Jinx

sorry, forgot about your requirement of uniqueness... just stick with the arrays method.

---

### Post by JinxAu on 2007-09-20
No worries... might take a break, then have a look at it again. :P

Thanks for the help!

Cya round
Jinx

---

### Post by bigboy_pdb on 2007-09-20
If it isn't necessary that you use awk then you can use the following command to extract the IP addresses at the front of the lines (I'm guessing that's what you want to do):
```

cat sample | grep -o '^\([[:digit:]]\{1,3\}\.\)\{1,3\}[[:digit:]]\{1,3\}' | sort | uniq

```

---

### Post by bigboy_pdb on 2007-09-20
Sorry, I realized that you were getting the IP addresses in the first two columns. So instead you could use:
```

cat sample | sed -n 's/^\(\([[:digit:]]\{1,3\}\.\)\{1,3\}[[:digit:]]\{1,3\}\) \(\([[:digit:]]\{1,3\}\.\)\{1,3\}[[:digit:]]\{1,3\}\).*/\1\n\3/p' | sort | uniq

```

---

### Post by ghostdog74 on 2007-09-20
> **bigboy_pdb said:**
> Sorry, I realized that you were getting the IP addresses in the first two columns. So instead you could use:
```

cat sample | sed -n 's/^\(\([[:digit:]]\{1,3\}\.\)\{1,3\}[[:digit:]]\{1,3\}\) \(\([[:digit:]]\{1,3\}\.\)\{1,3\}[[:digit:]]\{1,3\}\).*/\1\n\3/p' | sort | uniq

```
good effort. but couple of points...
1) No need for cat. sed takes in a file as input
2) sort has a unique option -u..
3) its just me i guess, but i absolutely dislike troubleshooting sed regexp like that if things go wrong.

there, 2 extra processes eliminated. now you have
```

sed -n 's/^\(\([[:digit:]]\{1,3\}\.\)\{1,3\}[[:digit:]]\{1,3\}\)  sample | sort -u

```

---

### Post by bigboy_pdb on 2007-09-20
JinxAu, the problem with your script was that it was printing all of the hashes each time there was a match on a line. For example, if there were two unique matches on the first line, they would be printed. If there was one new unique match on the second line, the two matches from the first line would be printed and then the new unique match would be printed, and so on. To fix this you need to add a block of code that has the form 'END { *code* }' and print the output from there. If you want to perform operations before going through each line then you can use 'BEGIN { *code* }'.

Your corrected code would look like this:
```

cat sample | awk '
# only match records starting with IP addresses
/^[0-9][0-9]*\.[0-9][0-9]*\.[0-9][0-9]*\.[0-9][0-9]*/  {
   
   # traverse each record and copy ip into host_address array if it does not already exist.
   for ( f = 1; f <= NF; ++f) {
      if ( $f ~ /[0-9][0-9]*\.[0-9][0-9]*\.[0-9][0-9]*\.[0-9][0-9]*/ && $f !~ /^255\./ ) {
         if ( ip_address[$f] != $f )
            ip_address[$f] = $f
      }
   }
}
END {
   # print our array of IP addresses.
   for ( hosts in ip_address )
      print "Our IP addresses are:", hosts, ip_address[hosts]
}'

```

---

### Post by bigboy_pdb on 2007-09-20
ghostdog74, that's good that it can be shortened. I'm used to using "echo -e" to send variables with multiple lines to sed so sometimes I forget to use it without piping the output of another command to it. Also, I wasn't aware of the "-u" option so thank you for mentioning it.

In your revision, you didn't write the full regular expression or write an end quote so it would have failed on the command line. It should be:
```

sed -n 's/^\(\([[:digit:]]\{1,3\}\.\)\{1,3\}[[:digit:]]\{1,3\}\) \(\([[:digit:]]\{1,3\}\.\)\{1,3\}[[:digit:]]\{1,3\}\).*/\1\n\3/p'  sample | sort -u

```

Good effort though ;)

---

### Post by JinxAu on 2007-09-20
> **bigboy_pdb said:**
> JinxAu, the problem with your script was that it was printing all of the hashes each time there was a match on a line. For example, if there were two unique matches on the first line, they would be printed. If there was one new unique match on the second line, the two matches from the first line would be printed and then the new unique match would be printed, and so on. To fix this you need to add a block of code that has the form 'END { *code* }' and print the output from there. If you want to perform operations before going through each line then you can use 'BEGIN { *code* }'.

Your corrected code would look like this:
```

cat sample | awk '
# only match records starting with IP addresses
/^[0-9][0-9]*\.[0-9][0-9]*\.[0-9][0-9]*\.[0-9][0-9]*/  {
   
   # traverse each record and copy ip into host_address array if it does not already exist.
   for ( f = 1; f <= NF; ++f) {
      if ( $f ~ /[0-9][0-9]*\.[0-9][0-9]*\.[0-9][0-9]*\.[0-9][0-9]*/ && $f !~ /^255\./ ) {
         if ( ip_address[$f] != $f )
            ip_address[$f] = $f
      }
   }
}
END {
   # print our array of IP addresses.
   for ( hosts in ip_address )
      print "Our IP addresses are:", hosts, ip_address[hosts]
}'

```

Ahh right... I forgot awk is treated like a big loop itself - hence the END statement. 

Thanks for your help bigboy and ghostdog... I am on the right track now.

Cya round
Jinx

---

