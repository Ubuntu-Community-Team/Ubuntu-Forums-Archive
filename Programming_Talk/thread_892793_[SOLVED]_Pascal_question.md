---
title: "[SOLVED] Pascal question"
date: 2008-08-17
forum: Programming Talk
---

### Post by cristo-father on 2008-08-17
Hi everbody.
I have a question.
I am trying to make a code that will write every character between an character c1 and a character c2. I tried this
```
Program  whatever (input,output);
var t,c1,c2:char;
begin
read(c1,c2);
if c1>c2 then 
		begin
			t:=c1;
			c1:=c2;
			c2:=t;
		end;
for t:=c1 to c2 do write(t:2);
writeln
end.
```
but it gives me this.
```
a d
   ! " # $ % & ' ( ) * + , - . / 0 1 2 3 4 5 6 7 8 9 : ; < = > ? @ A B C D E F G H I J K L M N O P Q R S T U V W X Y Z [ \ ] ^ _ ` a

```
How do i change the code to get what i want?
Thanks.

---

### Post by odyniec on 2008-08-17
My Pascal is a little rusty, but my guess would be that the program is reading the "a" and the " " (space) characters, instead of "a" and "d" as you might expect.

For a quick-and-dirty fix, you might just read the space into some variable:
```
read(c1,t,c2);
```

---

### Post by cristo-father on 2008-08-17
Thanks.
I am used to using spaces for integers and real numbers.

---

### Post by LaRoza on 2008-08-17
Thread title editted, see: [http://stopsayingretard.wordpress.com/](http://stopsayingretard.wordpress.com/)

---

