---
title: "Ruby &amp; Mysql"
date: 2010-04-21
forum: Programming Talk
---

### Post by Minky2k on 2010-04-21
Hi! I'm having some problems with a rubyscript that is accessing a mysql-database. When i'm trying to read ip-addresses from a textfile to an array and then base a sql-statement upon the array-elements I keep getting sql-statement errors due to ruby reads the textfile wrong and reads a newsline in the first two entries in the file. Does anyone have a solution for this problem? =)

_ip.txt_
```
10.199.198.1
10.199.198.2
10.199.198.3
```

_Error:_
```
update Hosts set `TM-Me`=0 where IP="10.199.198.1
";
update Hosts set `TM-Me`=0 where IP="10.199.198.2
";
update Hosts set `TM-Me`=0 where IP="10.199.198.3
";
```

_The SQL-statement should be:_
```
update Hosts set `TM-Me`=0 where IP="10.199.198.1";
update Hosts set `TM-Me`=0 where IP="10.199.198.2";
update Hosts set `TM-Me`=0 where IP="10.199.198.3";

```

 
_The Rubyscript:_
```
#!/usr/bin/ruby -w

   require "mysql"

   begin
     dbh = Mysql.real_connect("10.199.198.5", "root", "cisco", "hostlist")

     f = open("C:\\Users\\Lars\\Desktop\\ip.txt")
     
     ip_array = []
     f.each_line { |line| ip_array << line }
     index = 0
     until index == ip_array.length
     dbh.query ("update Hosts set `TM-Me`=0 where IP=\"#{ip_array[index]}\";\n")
     printf ("update Hosts set `TM-Me`=0 where IP=\"#{ip_array[index]}\";\n")
     index += 1
     end
     
     f.close

   ensure
     dbh.close if dbh
   end
```

---

### Post by escapee on 2010-04-21
It's not that Ruby is reading it wrong, but rather you are assuming each_line() does something it doesn't. Though there are more succinct ways for you to go about the whole thing, for a simple solution I would just change

```
f.each_line { |line| ip_array << line }
```

to 

```
f.each_line { |line| ip_array << line.chomp }
```

---

### Post by Minky2k on 2010-04-21
That fix you gave me worked great, stupid assumption of me. Thanks alot! =)

---

