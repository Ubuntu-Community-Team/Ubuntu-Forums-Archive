---
title: "how to open/change compiled file"
date: 2011-11-29
forum: Programming Talk
---

### Post by learnbash on 2011-11-29
Hello folks.

I have a compiled file i don't know its c base or what i don't have info of it, what i need to do is. I have few questions.

1. Is it possible i can open that compiled file and add some text under it?

2. Is it possible i can change a character "-abcd" to "-no_abcd". I have used below code,

```


sed -i 's/-abcd/-no_abcd/g' myfile


```

After that changes when i run file it give me segmentation fault error, please tell me what should i do in this case.

---

### Post by 11jmb on 2011-11-29
Why would you want to change a compiled binary? try this:

```
cat myfile
```

this is not source code, it is ones and zeros that your computer will read, which are pretty much meaningless to humans

---

### Post by learnbash on 2011-11-29
dear sir, i don't have its original file, so i can change code and recompile it, currently i need to change that thing after that everything will be perfect.

---

### Post by Simian Man on 2011-11-29
> **learnbash said:**
> 1. Is it possible i can open that compiled file and add some text under it?
What do you mean "text under it"?

> 2. Is it possible i can change a character "-abcd" to "-no_abcd".
If you wanted to change a string in the data segment of the executable to a smaller, or same sized string, it's possible.  But their is only so much space as needed for each string, so trying to replace it with a larger string likely won't work as you found out.

In general, mucking around with executable files is not a productive use of time.

---

### Post by ehmicky on 2011-11-29
Hi,
I'd add that if you don't have the source code, then it might be proprietary software and doing anything which might look like reverse-engineering is a legal-sensitive issue.

---

### Post by learnbash on 2011-11-29
no, actually our old programmer left and he is not giving source code to us thats why, problem is coming. so it means it is impossible.

---

### Post by 11jmb on 2011-11-29
Well, if there aren't any legal issues, why don't you just try reverse engineering?

---

### Post by learnbash on 2011-11-29
> **11jmb said:**
> Well, if there aren't any legal issues, why don't you just try reverse engineering?

respected sir, can you guide me how, i don't have any idea about that, can you give me proper guide line about that.

---

### Post by 11jmb on 2011-11-29
Wikipedia gives you a decent introduction to the process. If you are asking for guidelines on the legality, I am not 100% sure

[http://en.wikipedia.org/wiki/Decompiler](http://en.wikipedia.org/wiki/Decompiler)


I have used Boomerang in the past with some success
[http://boomerang.sourceforge.net/lostsource.php](http://boomerang.sourceforge.net/lostsource.php)

---

### Post by Simian Man on 2011-11-29
Legality is only an issue if someone would sue you.  That is almost never the case and doesn't seem to be the issue here.

I still am unsure what the OP's goal is.  What exactly do you want to change?  If it's just strings, you may be able to do that relatively easily.

---

### Post by ofnuts on 2011-11-29
> **learnbash said:**
> no, actually our old programmer left and he is not giving source code to us thats why, problem is coming. so it means it is impossible.If he's really your ex-programmer, the code is yours and not his, so sue him. Anyway you'll need this source code some day, so you have to secure it. You can't run a business using code that can break for who knows what stupid or legal reasons and no way to fix it without re-writing it all over (because it may not be a mere text patch next time).

---

### Post by learnbash on 2011-11-29
> **Simian Man said:**
> Legality is only an issue if someone would sue you.  That is almost never the case and doesn't seem to be the issue here.

I still am unsure what the OP's goal is.  What exactly do you want to change?  If it's just strings, you may be able to do that relatively easily.

yes sir only need to change the string, if it is possible please tell me, but remember when space create in file then it gives segmentation fault error, so how it possible, i am so thankful to you.

---

### Post by 11jmb on 2011-11-30
To change something simple like a single string Boomerang should work for you.

Ofnuts raises an excellent point, though. If this guy was your employee, then you own every line of code he wrote for you. Getting your hands on the source will always be the most powerful solution.

---

### Post by learnbash on 2011-12-01
> **11jmb said:**
> To change something simple like a single string Boomerang should work for you.

Ofnuts raises an excellent point, though. If this guy was your employee, then you own every line of code he wrote for you. Getting your hands on the source will always be the most powerful solution.

can you tell me or give me link which Boomerang software will help me.

---

### Post by 11jmb on 2011-12-01
> **learnbash said:**
> can you tell me or give me link which Boomerang software will help me.

[http://boomerang.sourceforge.net/](http://boomerang.sourceforge.net/)

---

### Post by nvteighen on 2011-12-01
> **learnbash said:**
> no, actually our old programmer left and he is not giving source code to us thats why, problem is coming. so it means it is impossible.

> **ofnuts said:**
> If he's really your ex-programmer, the code is yours and not his, so sue him. Anyway you'll need this source code some day, so you have to secure it. You can't run a business using code that can break for who knows what stupid or legal reasons and no way to fix it without re-writing it all over (because it may not be a mere text patch next time).

Not necessarily. It might depend on the contract and the country's legal system whether copyright of work done by some company's employees is automatically assigned to the company. IIRC, in the Western world, the employers have to explicitly waive their copyright rights on their company; otherwise, the employer keeps them. 

Anyway, this is exactly the kind of issues your company's lawyers are for... They'll know much better than we do. Or hire a lawyer if this is program is so important for you.

Now, onto the technical issue... a decompiler won't give you C code, though. It will give you the ASM code... which is really hard to manage... You can modify and understand ASM, but you'll probably need to hire some ASM-guru to do it depending on the program's complexity. I'd rather hire a lawyer instead and try to have your ex-employee hand in the source to you :P

---

