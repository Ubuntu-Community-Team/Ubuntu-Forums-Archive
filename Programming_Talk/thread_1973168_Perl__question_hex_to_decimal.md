---
title: "Perl : question hex to decimal"
date: 2012-05-04
forum: Programming Talk
---

### Post by alexfish on 2012-05-04
this works from the command line
```
perl -e 'print join(",",map { join(".", unpack("C4", pack("L", hex))) } split /,/, shift),"\n"' 4d92124d,fcffffff,4e92124d,4e92124d,470d5c1,c60f4382  
```gives```
77.18.146.77,255.255.255.252,77.18.146.78,77.18.146.78,193.213.112.4,130.67.15.198
```Need help on putting this in to perl script

thanks in advance

alexfish

---

### Post by 11jmb on 2012-05-04
What you have is pretty much a very condensed perl script

just get rid of the "perl -e", add 
```
#!/usr/bin/perl
``` 
to the top of your script, and save it as a .pl file.

Are you looking to take in user input or command line args for the script?

---

### Post by alexfish on 2012-05-04
have tried removing as said + remove semi colons but produces  errors
IE: ```
Bareword found where operator expected at ./convert.pl line 2, near "470d5c1"
    (Missing operator before d5c1?)
```
thought the way it written the command is working on the data 4d92124d,IE 'command struct' fcffffff,4e92124d,4e92124d,470d5c1,c60f4382

though may be  @array or $str = data , would work but don't know how or were to place it

thanks ,know how to pass argv

alex

---

### Post by alexfish on 2012-05-06
Found a way to do it 

```
#!/usr/bin/perl
my $hex_info = "4d92124d,fcffffff,4e92124d,4e92124d,470d5c1,c60f4382";
my $dec_info = `perl -e 'print join(",",map { join(".", unpack("C4", pack("L", hex))) } split /,/, shift),"\n"' $hex_info` ;
print $dec_info
```

alexfish

---

### Post by 11jmb on 2012-05-07
That's a way to do it, but invoking the perl interpreter inside a script is pretty ugly. You can just replace the last line of your script.

```

#!/usr/bin/perl
my $hex_info = "4d92124d,fcffffff,4e92124d,4e92124d,470d5c1,c60f4382";
print join(",",map { join(".", unpack("C4", pack("L", hex))) } split(/,/, $hex_info)), "\n";

```

And obviously, hex_info does not have to be hard-coded, it can be passed in with argv

---

### Post by alexfish on 2012-05-07
I know it's Ugly to look at at first instance , But will explain .

this script fits on client side  and the arg is been sent by the  server , and client has to reply with the decoded message , + other

so yes the argv is important to the script , , at present it is the only solution at hand at the moment "no different than processes control" can also achieve same with bash script ,  not  much Knowledge of perl , boy there are some weird things to get to grips with.

It will have to do for now till get a bit more Knowledge ,

could even use this type type of code as a dispatcher / it common method in programming . its a bit like a postman

---

