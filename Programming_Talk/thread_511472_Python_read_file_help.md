---
title: "Python read file help"
date: 2007-07-27
forum: Programming Talk
---

### Post by crashovaride on 2007-07-27
Hi all,

I'm trying to write a python application which will read from a file, and add to the strings it reads, this is what i have so far, and everything i have tried, it will not append to the string...


data_file = open('/root/Desktop/social.log', 'rb')
for line in data_file:
	print line
	filehandle = open ('/root/Desktop/config.log', 'a')
	filehandle.write (line + "ending of string")
data_file.close()
filehandle.close()

Where the "ending of string" is, is where i want to add to line. So, if line is "hello " i would want it printed in the file as "hello ending of string" As all i could get it to do was "ending of string hello" and i would like to place it the other way.

Any ideas? Can anyone please help?

Thank you, 
Crash.

---

### Post by pmasiar on 2007-07-27
First, use [ code ] ... [ / code ] tags:

```

data_file = open('/root/Desktop/social.log', 'rb')
for line in data_file:
	print line
	filehandle = open ('/root/Desktop/config.log', 'a')
	filehandle.write (line + "ending of string")
data_file.close()
filehandle.close()

```
> **crashovaride said:**
> Hi all,
Where the "ending of string" is, is where i want to add to line. So, if line is "hello " i would want it printed in the file as "hello ending of string" As all i could get it to do was "ending of string hello" and i would like to place it the other way.


1) You opened input file to read in binary mode, I believe *NOT* what you intended :-)
2) You are opening the same output file for append (text mode) multiple times. You probably want to do it outside of the loop, just once.
3) Nitpick: better names help *YOU* to understand your code better. Like input_file and output_file 
4) you probably want to append only to some input string, not all? Maybe skip printing some?

---

### Post by crashovaride on 2007-07-27
Well, what i'm looking to get is the entire listing, and change the output to all.

---

### Post by dwblas on 2007-07-30
I haven't tested this but it should be close to what you want.```
data_file = open('/root/Desktop/social.log', 'r')
filehandle = open ('/root/Desktop/config.log', 'a')
for line in data_file:
	print line
        line = line.replace( "\n", "" )         ## strip newline
	filehandle.write ( "%s %s\n" % (line, "ending of string"))
data_file.close()
filehandle.close()
```

---

### Post by trwww on 2007-07-31
Hello,

Just to compare, heres one way to do it in perl:

```

use IO::File;

$input  = IO::File->new('>> /root/Desktop/config.log');
$output = IO::File->new('< /root/Desktop/social.log');

while (my $line = $input->getline) {
  chomp $line;
  $output->print( "$line ending of string\n" );
}
```

Regards,

trwww

---

