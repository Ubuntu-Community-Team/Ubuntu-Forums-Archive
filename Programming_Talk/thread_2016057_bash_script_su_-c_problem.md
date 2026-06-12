---
title: "bash script su -c problem"
date: 2012-07-04
forum: Programming Talk
---

### Post by Drenriza on 2012-07-04
Hey guys.

Anyone who can tell me how i can make this command work in my bash script

```
su my_user -c 'strexp SYSTEM | awk -F '"' '{print $2}' > /home/my_user/hotelNavn'
```

the error i get is as follows.
```
./Script: line 42: unexpected EOF while looking for matching `''
```

Thanks on advance.
Kind regards.

---

### Post by codemaniac on 2012-07-04
> **Drenriza said:**
> Hey guys.

Anyone who can tell me how i can make this command work in my bash script

```
su my_user -c 'strexp SYSTEM | awk -F '"' '{print $2}' > /home/my_user/hotelNavn'
```

the error i get is as follows.
```
./Script: line 42: unexpected EOF while looking for matching `''
```

Thanks on advance.
Kind regards.

How about escaping the " in the below awk separator  .

```
su my_user -c "strexp SYSTEM | awk -F'\"' '{print $2}' > /home/my_user/hotelNavn"
```

---

### Post by SeijiSensei on 2012-07-04
I noticed you snuck that other change, from single to double quotes, in there, too!

Drenriza, the problem was that the quotes didn't match up.  Unless I'm using environment variables, I'll usually wrap the command in double quotes and use single quotes for things within the command like awk.  This won't work if the command needs to expand environment variables and thus requires the parameters to be inside double quotes themselves.  In that case you have to escape the double quotes within the command with "\".

---

### Post by codemaniac on 2012-07-04
> **SeijiSensei said:**
> I noticed you snuck that other change, from single to double quotes, in there, too!

Drenriza, the problem was that the quotes didn't match up.  Unless I'm using environment variables, I'll usually wrap the command in double quotes and use single quotes for things within the command like awk.  This won't work if the command needs to expand environment variables and thus requires the parameters to be inside double quotes themselves.  In that case you have to escape the double quotes within the command with "\".

Yeah good catch ;)
I also prefer the same strategy while dealing with variables .

---

### Post by Drenriza on 2012-07-05
> **SeijiSensei said:**
> I noticed you snuck that other change, from single to double quotes, in there, too!

Drenriza, the problem was that the quotes didn't match up.  Unless I'm using environment variables, I'll usually wrap the command in double quotes and use single quotes for things within the command like awk.  This won't work if the command needs to expand environment variables and thus requires the parameters to be inside double quotes themselves. **In that case you have to escape the double quotes within the command with "\"**.

Can you give me an example, i'am totally not following :) i'am not that into awk again :(

---

### Post by SeijiSensei on 2012-07-05
Let's start with your original code:

```
su my_user -c 'strexp SYSTEM | awk -F '"' '{print $2}' > /home/my_user/hotelNavn'
```

This line poses problems for the parser.  Is the single quote after -F the one that matches the initial single-quote?  One simple solution is to use double quotes around the command and single quotes inside 

```
su my_user -c "strexp SYSTEM | awk -F '"' '{print $2}' > /home/my_user/hotelNavn"
```

This is better, but it still won't work because the parser will want to associate the double quote after -F with the one at the beginning of the command.  So to avoid that problem, you need to escape the double quote after -F like this:

```
su my_user -c "strexp SYSTEM | awk -F '\"' '{print $2}' > /home/my_user/hotelNavn"
```

Now it's clear to the parser that it should treat the double quote after -F as a literal, since it is escaped, and that the double quote at the end of the command matches the one at the beginning.

Does that help clarify things?

---

### Post by codemaniac on 2012-07-05
great explanation SeijiSensei .Could not have explained it better .

---

### Post by Drenriza on 2012-07-06
[quote]Does that help clarify things?[quote]

Thanks for the explanation.

Uhm when i try and execute the command form the root user i get a error saying that the **bash: strexp: command not found** but if i log in as the user and run the same command, their is no trouble. Any ideas to what the cause of the error could be?

---

### Post by codemaniac on 2012-07-06
> **Drenriza said:**
> [quote]Does that help clarify things?[quote]

Thanks for the explanation.

Uhm when i try and execute the command form the root user i get a error saying that the **bash: strexp: command not found** but if i log in as the user and run the same command, their is no trouble. Any ideas to what the cause of the error could be?try running **strexp** with absolute path .```
**which ****strexp** 
```

The above would return absolute path of [B]strexp .
[/B]

---

### Post by Drenriza on 2012-07-06
> **codemaniac said:**
> [QUOTE=Drenriza;12079489][quote]Does that help clarify things?try running **strexp** with absolute path .```
**which ****strexp** 
```

The above would return absolute path of [B]strexp .
[/B]

Aaa yes and use it with the su command. ty ty

---

### Post by Drenriza on 2012-07-06
Uhmm the strexp command now works, but the awk part if being completely ignored. Since it's not printing $2 and using " as a delimiter. To get the text between the two "text".

---

### Post by codemaniac on 2012-07-06
Basically I am not familiar with the "strexp" utility and hence have no idea how your output looks like .You may have to choose the awk separator wisely .

Can you please post your strexp output ?

---

### Post by Drenriza on 2012-07-06
> **codemaniac said:**
> Basically I am not familiar with the "strexp" utility and hence have no idea how your output looks like .You may have to choose the awk separator wisely .

Can you please post your strexp output ?

Output
SYSTEM    	"**text text some name**" username /dev/ttyxx EN xx

The bold text is what i want to grab. In my initial post, the command works by hand as the correct user, no trouble. But have had difficulties (as you know) now when i try and make the same thing work as root with the su -c command.

---

### Post by codemaniac on 2012-07-06
In order to keep things simple and not indulge into so many quote mess ups you can try keeping all the awk commands in a .awk script .

```

cat awklet.awk
```
```

#!/bin/awk

BEGIN{
FS = "\"" ;
}

{
print $2 ;
}

```
```
su my_user -c "strexp SYSTEM | awk -f awklet.awk"
```

---

### Post by SeijiSensei on 2012-07-06
> **Drenriza said:**
> Output
SYSTEM    	"**text text some name**" username /dev/ttyxx EN xx

The bold text is what i want to grab. In my initial post, the command works by hand as the correct user, no trouble. But have had difficulties (as you know) now when i try and make the same thing work as root with the su -c command.

So you want to take the result and create the string "text text some name" from the items 2-5 of the output?  Use this:

```
strexp SYSTEM | awk '{print "\"" $2 " " $3 " " $4 " " $5 "\""}'
```

---

### Post by codemaniac on 2012-07-06
> **SeijiSensei said:**
> So you want to take the result and create the string "text text some name" from the items 2-5 of the output?  Use this:

```
strexp SYSTEM | awk '{print "\"" $2 " " $3 " " $4 " " $5 "\""}'
```

SeijiSensei ,

is there any specific specific reason for not choosing a " as separator .The below would also do the job .

```
strexp SYSTEM | awk -F\" '{print $2}'
```

---

### Post by SeijiSensei on 2012-07-06
Since I can't find the strexp command on my machine, I'm not entirely clear on what Drenriza is trying to accomplish.  I couldn't tell whether the quotes are in the string he's trying to parse, or whether he wants the resulting string to be embedded in quotes.  I agree that your method works fine if the input string is

```
stuff "more stuff" still more stuff
```

Then your method returns 'more stuff' without any surrounding quotation marks since the double-quote is serving as the awk delimiter.

```
echo 'stuff "more stuff" still more stuff' | awk -F\" '{print $2}'
more stuff

```

---

### Post by codemaniac on 2012-07-06
Me too dont have any idea what does strexp  command actually do .
However in  post no #13 OP has mentioned his output like below 

> SYSTEM "**text text some name**" username /dev/ttyxx EN xx

And he wants to slice out the bold string series .In this case the below would serve the requirement .

```
echo 'SYSTEM "text text some name" username /dev/ttyxx EN xx' |  awk -F\" '{print $2}'
```

---

### Post by Drenriza on 2012-07-11
Hey guys.

Thanks for all the help.

The command now works and i execute it in my java program as follows.

```
Process process = Runtime.getRuntime().exec(new String[] { "bash", "-c", "/bin/su nice -c \"" + "/home/nice/bin/strexp system\"" +
                    " |/usr/bin/awk -F\\" + "\"" + " '{print $2}'"});
```

Kind regards.

---

