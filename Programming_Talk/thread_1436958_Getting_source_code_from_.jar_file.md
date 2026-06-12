---
title: "Getting source code from .jar file"
date: 2010-03-23
forum: Programming Talk
---

### Post by hyperAura on 2010-03-23
Hello people, I have created a game in Java and I have also created its executable .jar file in order to be able to send it to people to test it themselves.. 

My question is if it is possible for them to get the source code from the .jar file which is something I do not desire after all the effort I have placed into it.. Thnx :)

---

### Post by slakkie on 2010-03-23
A jar file is basicly a zip file, so getting to the .class files should be easy;

jar -xf myApp.jar

Then you have all the .class files, and you can use jad ( [http://www.varaneckas.com/jad](http://www.varaneckas.com/jad) ) to decompile the .class files into source code. 

Please be aware that the source code now has no comments and is harder to reda due to cryptic names ala public function functionA(String stringA)  etc etc. But at least you can have a peak at the code.

It saved my *** once in college when I removed all my source code and only had my compiled .class files. Best of luck!

---

### Post by hyperAura on 2010-03-23
so is there another way to distribute the java program in order not to be able for the receiver to get its source code?

---

### Post by nvteighen on 2010-03-23
> **hyperAura said:**
> so is there another way to distribute the java program in order not to be able for the receiver to get its source code?

Even natively compiled code can be disassembled. Ok, the resulting code isn't trivial to read, but it can be read by a trained eye. There's nothing such as complete "source security" and no reason for it either: You can't stop an expert from getting your source whatever you do to prevent it, and will you bother about the average end user that just wants your program to work?

No, encryption doesn't work because in order to have the application running, it'll need an intermediate layer that decrypts it...

---

### Post by hyperAura on 2010-03-23
in my case this is not so important but I was just looking a bit more deeper on this..

so for example if I want to sell some software the only way to force the buyer is by showing the features of the program face to face or sending him a demo program with limited features.. is that correct?

---

### Post by lykeion on 2010-03-24
I agree with nvteighen, there is no way you can protect your code from a person who really sets his mind to get the source.
Usually you obfuscate the code with proguard or similiar obfuscator and leave it to that. 
See [http://developers.sun.com/mobility/midp/ttips/midletsize]("http://developers.sun.com/mobility/midp/ttips/midletsize")

But I am no believer in hiding source at all costs either. 
I think it can be more profitable in the long run opening up your code, inviting other programmers to join you in making the application better (or game or whatever you're developing).

---

### Post by nvteighen on 2010-03-24
> **hyperAura said:**
> 
so for example if I want to sell some software the only way to force the buyer is by showing the features of the program face to face or sending him a demo program with limited features.. is that correct?

Nope... there's a much smarter model which is Red Hat's: Sell services, not code. This means, ok, you can get Red Hat from anywhere because it's Free Software and people are allowed to redistribute it either for free or not. But, only buying it at the Red Hat's official website will give you access to their own official support.

---

### Post by hyperAura on 2010-03-25
cool, thnx for your replies.. well im not against open source but atm im at uni and i hate it when other people copy my code and get the marks without even working for it..

---

### Post by HotCupOfJava on 2010-03-25
I might be in error, but I believe that Java's licensing requires you to make the source code available for any program you distribute. Maybe check your license?

---

### Post by CptPicard on 2010-03-25
> **HotCupOfJava said:**
> I might be in error, but I believe that Java's licensing requires you to make the source code available for any program you distribute. Maybe check your license?

Umm, no. That's wrong :)

---

### Post by wmcbrine on 2010-03-26
> **hyperAura said:**
> cool, thnx for your replies.. well im not against open source but atm im at uni and i hate it when other people copy my code and get the marks without even working for it..And that actually happens, does it?

---

### Post by nvteighen on 2010-03-26
> **hyperAura said:**
> cool, thnx for your replies.. well im not against open source but atm im at uni and i hate it when other people copy my code and get the marks without even working for it..

Lock up your computer? Store the code in some USB so that it isn't saved on the hard disk? Encrypt the source?

Man, this is something that will happen no matter what you study, no matter where. Those are the situations in which the professor has to be a good one and not only ask for the code but ask for an explanation of how it works. If someone copied it, chances are high that person doesn't know how it works, making it obvious that he copied.

---

### Post by HotCupOfJava on 2010-03-26
Then I stand corrected!

---

### Post by hyperAura on 2010-03-26
plagiarism is something which happens a lot especially in subjects such as cs.. the big problem is that if u r caught for that it doesn't matter if you are the owner or the copier.. u might get kicked out of uni because someone else copied from u.. :(

---

### Post by wmcbrine on 2010-03-26
Don't talk in generalities -- has it happened *to you*? (You implied that it had, and was ongoing -- "I hate it when other people copy my code...".) Do you have reason to think that it would? And how would people get hold of your schoolwork code, anyway?

---

### Post by hyperAura on 2010-03-26
yes it has happened before but the school did not realize it.. other students that were caught were kicked out of the school.. the latest project i've done is my final year project and yes i have reason to believe that people would copy as the algorithms used are core in programming other games too..

i don't know how you can break into a linux account without knowing the password but people have done it as i've seen my code before changing hands.. and i have changed my password a few times..

this time i have not uploaded my files on the school machines yet but at some point i will have to..

---

