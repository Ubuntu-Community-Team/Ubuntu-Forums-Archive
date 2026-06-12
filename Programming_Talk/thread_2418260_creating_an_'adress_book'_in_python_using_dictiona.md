---
title: "creating an 'adress book' in python using dictionaries - extending the script ..."
date: 2019-05-04
forum: Programming Talk
---

### Post by dilbert_one on 2019-05-04
hello dear fellow ubuntu-users, 




i am currently creating  an 'adress book' python where i want to use dictionaries?


**the plan:**
I'm trying to create an little adress-book that has got an index  the index - think would be apropiate - could be the  'nickname' in the adress-book 
I want to give some options: 


with the nickname the user can do some savings:


a. save a name of a person, the address of a person and subsequently the  phone-number of that person.well - so far so good: - i want to use use a dictionaries, i want to have such a list. e.g




```
myList = [["Bill","Butcher", "4433345411"],["Billiboy","2 Rue Rivoli ", "0994399394800838383"]]

``````


And then if I wanted to see a certain contact I would just use some more code to search for a pattern. And then i need to figure out how to do it with a dictionary?


well - i could do some starting points  - with the usage of a dictionary: 
i could probably start with this:






```
my_dict = {"Don": {"name": "Donald Jones", "address": "1 Rue Rivoli Paris ", "phone": "9444444411"}, 
           "Joseph": {"name": "Joseph Boy", "address": "3 Tivoli Paris", "phone": "0800838383"}
            "Bilbo": {"name": "Bilbo Baggin", "address": "4 White House Washington", "phone": "08055550838383"}
         
         }
         

```

But how to get access to the records that i have created: well i can access records using




```


my_dict["Don"]["name"]

``````




or like so


```
my_dict["Bilbo"]["phone"]

```

by the way: Keys in a Python dictionary tend to be  unique. Having a list of contacts in my adressbook the important thing is - there should be no name twice.  That saind - we see that  i can have the solution like this:




```
contacts = {}
contacts['Don'] = ["1 Rue Rivoli", 9444444411]
contacts['Joseph'] = ["3 Tivoli", 0800838383]

```



so adding data to a dictionary is based on the access operator []. 


the question is: how to extend the scipt a bit
should i make use of 


- raw input
- arg.pop 


how would you extend the script!?


what do you say!?




love to hear from you

---

### Post by TheFu on 2019-05-04
Since nobody else responded .... 

I dont know python. I do perl and ruby.  If a "dictionary" is similar to a hash in perl, then the keys must be unique.  Usually, that is difficult using any sorts of names.  You could use email addresses or phone numbers, but every entry would require one.

Address <--- is the correct spelling in English. ;)
Address books need some sort of external DB. Editing code to modify names is crazy.  Use a file, DB, LDAP, something external.
I would avoid JSON, XML, YAML, though using YAML might be the easiest, to read and write.

In Perl, I'd use either a CSV file and read the entire thing into RAM, then if it was modified, lock it using flock, and write it out at program close. That would work for 1-10 users. 

For more than that, a real DB is needed.  SQLite would probably be sufficient. Learning to use an ORM is a good thing and worth the effort on a trivial first example like an address book.  DO NOT WRITE SQL directly in your code.  Hackers love it when people have raw SQL in their code.  Let the ORM handle that stuff.

I know you want to write this in python, but a single text file with specific columns (delimited by | ) and using grep is probably sufficient.  It is very nice to search an entire group of entries for the answer ... a few letters/numbers found anywhere on the "record" ... a line, would cause that line to be displayed.

**addr.data** contains:```

"Don"|"Donald Jones"|"1 Rue Rivoli Paris "|"9444444411"
"Joseph"|"Joseph Boy"|"3 Tivoli Paris"|"0800838383"
"Bilbo"|"Bilbo Baggin"|"4 White House Washington"|"08055550838383"
```

You can have python read the file and search each line, if you like, or use egrep.
```

$ egrep -i wash addr.data 
"Bilbo"|"Bilbo Baggin"|"4 White House Washington"|"08055550838383"

$ egrep -i paris addr.data 
"Don"|"Donald Jones"|"1 Rue Rivoli Paris "|"9444444411"
"Joseph"|"Joseph Boy"|"3 Tivoli Paris"|"0800838383"
```

The found lines could easily be formatted, thanks to the delimiter.
```

nickname: Don
    name: Donald Jones
    address: 1 Rue Rivoli Paris 
    phone: 9444444411
```
Reading the output from a different process is trivial in perl.
```
   open(ADDR, "egrep -i  \"$search\"  "$datafile" >&1 |") or die "Can't open address file: $!\n";
       while (<ADDR>){
# do stuff with each line
      }
      close(ADDR);
 
```
I bet python has a way too.

Sometimes the easy answer is the best. Just depends on the requirements.  

On Unix, text is the default DB, unless you have a specific reason NOT to use it.  That is part of the Unix philosophy [https://en.wikipedia.org/wiki/Unix_philosophy](https://en.wikipedia.org/wiki/Unix_philosophy) .
> summarized by Peter H. Salus in A Quarter-Century of Unix (1994):[1]

    Write programs that do one thing and do it well.
    Write programs to work together.
    Write programs to handle text streams, because that is a universal interface.

 I keep lots of text files with single-record data here. Then just use egrep to search them. Been doing that for 25+ yrs and never needed to worry about some DBMS failing or the data being unavailable due to some change on the system.  I have moved sensitive data into different password managers over all these years - can search text inside those just as easily.

Following the Unix Philosophy has prevented me from doing dumb things hundreds of times.

---

### Post by dilbert_one on 2019-05-06
hello dear TheFu 

many many thanks for the quick and in depth going answer. You have helped me alot and gave me many many good hints. 

i do not know perl very good.  And i am also at the starting point with Python. 

So i am very glad for any and all help. 

You have helped me - and you encouraged me in going on. 

Many many thanks! 

have a great day!!

---

