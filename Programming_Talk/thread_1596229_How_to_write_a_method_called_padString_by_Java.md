---
title: "How to write a method called padString by Java?"
date: 2010-10-14
forum: Programming Talk
---

### Post by hector_ronado on 2010-10-14
Does anyone know how to write this padString method?

write a method called padString that accepts two parameters: a string and an integer representing a length. the method should pad the parameter string with spaces until its length is the give length.

 for example: padString("hello", 8 ) should return "hello     " (with three spaces after hello)

I have been asking to write the method without using any main() and system words in the method.

For now, I have write it like this.

    public static String padString(String x, int y){
       
       return String.format("x",y);
    }

It is probably totally wrong, but that's all I can do for now...

Can anyone teach me how to do it?

Thank you.

---

### Post by schauerlich on 2010-10-14
Obvious homework is obvious.

---

### Post by akoskm on 2010-10-14
> **hector_ronado said:**
> Does anyone know how to write this padString method?

write a method called padString that accepts two parameters: a string and an integer representing a length. the method should pad the parameter string with spaces until its length is the give length.

 for example: padString("hello", 8 ) should return "hello     " (with three spaces after hello)

I have been asking to write the method without using any main() and system words in the method.

For now, I have write it like this.

    public static String padString(String x, int y){
       
       return String.format("x",y);
    }

It is probably totally wrong, but that's all I can do for now...

Can anyone teach me how to do it?

Thank you.

It's enought to pint the word and to calculate the difference between the given number and x.lenght(), then just print the spaces.

---

### Post by hector_ronado on 2010-10-14
> **schauerlich said:**
> Obvious homework is obvious.

Hmm... Yea! It is a homework. So what? I wasn't here to ask for solution without trying... I was having problem with my homework, so is it any problem with that's a homework?

---

### Post by hector_ronado on 2010-10-14
> **akoskm said:**
> It's enought to pint the word and to calculate the difference between the given number and x.lenght(), then just print the spaces.

Can you said it more detail? Cause I don't really know what you means... Sorry about my poor English...lol

---

### Post by schauerlich on 2010-10-14
> **hector_ronado said:**
> Hmm... Yea! It is a homework. So what? I wasn't here to ask for solution without trying... I was having problem with my homework, so is it any problem with that's a homework?

[Yes](http://ubuntuforums.org/showthread.php?t=717011).

tl;dr no homework questions

---

### Post by hector_ronado on 2010-10-14
> **schauerlich said:**
> [Yes]("http://ubuntuforums.org/showthread.php?t=717011").

tl;dr no homework questions

Sorry... it's my bad. I didn't know we can't ask homework here...

---

### Post by slooksterpsv on 2010-10-14
We can give you advice, I believe, like you'll use if statements or you'll check the length, not program it for you but help you understand how it should flow, am I wrong on that?

EDIT: just made the program in python hehe =P

---

### Post by lisati on 2010-10-14
> **hector_ronado said:**
> Sorry... it's my bad. I didn't know we can't ask homework here...
From the [forum code of conduct]("http://ubuntuforums.org/index.php?page=policy"):

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

### Post by hector_ronado on 2010-10-14
> **slooksterpsv said:**
> We can give you advice, I believe, like you'll use if statements or you'll check the length, not program it for you but help you understand how it should flow, am I wrong on that?

Hmm... I don't really get what did you mean...

---

### Post by lisati on 2010-10-14
> **hector_ronado said:**
> Hmm... I don't really get what did you mean...

I think [this]("http://www.rgagnon.com/javadetails/java-0448.html") is what you're after.

---

