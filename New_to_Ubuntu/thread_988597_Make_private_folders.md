---
title: "Make private folders?"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-11-20
is there anyway i can make a private folder or change privilages for people on ubuntu? i have a 4chan /b/ folder and i dont want people to see it because it has some gore and nsfw material

---

### Post by taurus on 2008-11-20
If you don't want other to access that directory, you can change the permissions.

```
chmod 700 *name_of_directory*
```

Then, nobody can access that directory except you since you are the owner of that.

---

### Post by mr-Kirch on 2008-11-20
> **taurus said:**
> If you don't want other to access that directory, you can change the permissions.

```
chmod 700 *name_of_directory*
```

Then, nobody can access that directory except you since you are the owner of that.

i dont know what the directory is though, the folder is called "b" without quotes and its under my home folder>>pictures

---

### Post by SuperSonic4 on 2008-11-20
> **mr-Kirch said:**
> i dont know what the directory is though, the folder is called "b" without quotes and its under my home folder>>pictures

```
~/pictures/b
```

---

### Post by mr-Kirch on 2008-11-20
k thanks

---

### Post by Paqman on 2008-11-20
If you're running Intrepid then you can have a private folder that is not just private, but actually encrypted.

Just run:
```

ecryptfs-setup-private

```

To set it up. It's not mounted by default, but just and click on the script in the folder to mount it.

---

### Post by hyper_ch on 2008-11-20
well, making the folder accessible only to you by relaying on the unix permissions will not prevent anyone from getting those files with physical access.

---

### Post by Paqman on 2008-11-20
> **hyper_ch said:**
> well, making the folder accessible only to you by relaying on the unix permissions will not prevent anyone from getting those files with physical access.

Hence the new encrypted folder in the user's home. You can even give it it's own password.

Truecrypt is a good way to create encrypted folders, if you want something a little more flexible.

---

### Post by fiendishfish on 2008-11-20
> **hyper_ch said:**
> well, making the folder accessible only to you by relaying on the unix permissions will not prevent anyone from getting those files with physical access.

I agree that setting permissions isn't the best way, if someone really wanted to read the contents, they would be able to. I also recommend truecrypt, this will hinder family/friends etc a lot, maybe even feds!

On a side note, I don't think telling us the contents of the directory is really relevant, I am sure a lot of people probably judged you on being a /b/tard!, or maybe you are making some silly attempt at trolling?

---

### Post by hyper_ch on 2008-11-21
> **Paqman said:**
> Hence the new encrypted folder in the user's home. You can even give it it's own password.

I prefer fulldisk encryptiion - don't have to worry anymore where I put what :)

---

### Post by fiendishfish on 2008-11-21
> **hyper_ch said:**
> I prefer fulldisk encryptiion - don't have to worry anymore where I put what :)

But obviously he can't encrypt his fulldisk otherwise the people he's worried about can't go on his pc, unless he has some cool partionage.

---

### Post by y@w on 2008-11-21
> **fiendishfish said:**
> I agree that setting permissions isn't the best way, if someone really wanted to read the contents, they would be able to. I also recommend truecrypt, this will hinder family/friends etc a lot, maybe even feds!

Haha if someone really, really wanted to read the contents, they would be able to with an encrypted disk too. Given enough time and enough computing power that can be broken as well :)

---

### Post by hyper_ch on 2008-11-21
> **y@w said:**
> Given enough time and enough computing power that can be broken as well :)
how many years? With todays encryption tools adding 100 mio more computers doesn't have a large impact on brute-forcing...

---

### Post by fiendishfish on 2008-11-21
> **y@w said:**
> Haha if someone really, really wanted to read the contents, they would be able to with an encrypted disk too. Given enough time and enough computing power that can be broken as well :)

Not really, he is obviously trying to hide the folder from his parents or family whoever use the computer, and seeing as they probably don't have Scotland Yard or the FBI behind them, it is practically impossible.

And if he's using a ridiculously large complex password it is probably near impossible for ANYONE, afaik.

-fiendishfish

---

### Post by hyper_ch on 2008-11-21
I know, this is not quite how it works but lets look at some numbers:

Number of possible chars:
a-z = 26
A-Z = 26
0-9 = 10
--> 62 (more is possible with chars like öäüéàèç*+§°$}[........)
Let's say you have easily 100 possible character (should be a lot more actually)

Now you take a 20 key long password, that will result in

100²&#8304; possible combinations

Let's say, you have 1 mio computers available --> 100³
Let's also assume they can test 10'000 combinations per second --> 100²

This means, it will still take 100¹&#8309; seconds to try every combination.

So even if you have 100 mio computers it will not make a huge difference.

---

### Post by scorp123 on 2008-11-21
> **hyper_ch said:**
> This means, it will still take 100¹&#8309; seconds to try every combination.  100^15 seconds = 1000000000000000000000000000000

... divided by 3600 we get the number of hours ...
... divided by 24 we get the number of days ...
... divided by 365 we get the number of years ...

If I calculated correctly:

100^15 seconds == 31'709'791'983'764'586'504'312 years


Yeap, that should keep 'em busy :)

---

### Post by houbysoft.xf.cz on 2008-11-21
Yeah but anyway I guess he would not choose a 20 char long password :) my guess would be a just regular chars and like 5-10 chars long. That would not take so long :)

---

### Post by y@w on 2008-11-21
> **hyper_ch said:**
> how many years? With todays encryption tools adding 100 mio more computers doesn't have a large impact on brute-forcing...


Wow, that was supposed to be a joke, as indicated by the smiley face. Someone said that if they really wanted to get into these files that they should encrypt it. I just took it one step further since they *really* did want to get into it. I didn't think it was going to bring out so much math :) Though, it was partially true. We said the same thing about DES years ago so they went to 3DES. Then they went to AES. Yes, it's practically impossible to get into an encrypted disk/file in a reasonable amount of time, but that doesn't mean this "secret" is safe forever. If someone "really, really" wanted to they could throw a few billion dollars at it and get themselves a little cluster on Amazon EC2.. Let just hope this person isn't related to Bill Gates :)

---

### Post by hyper_ch on 2008-11-22
as shown, 100 mio cpus that can test 10'000 passwords a second don't have a huge impact with a reasonable long password... much more likely to break encryption if a weakness in the algorithm is found...

---

### Post by fiendishfish on 2008-11-22
> **houbysoft.xf.cz said:**
> Yeah but anyway I guess he would not choose a 20 char long password :) my guess would be a just regular chars and like 5-10 chars long. That would not take so long :)

Well, no sensible person would use a 5-10 character password if it was protecting important files, but with something as useless as /b/...

Although,it could be more 'renowned' images from /b/ which certainly may get you in trouble, thus increasing the need for strong encryption with strong passwords.

-- fiendishfish

---

### Post by scorp123 on 2008-11-22
> **houbysoft.xf.cz said:**
> Yeah but anyway I guess he would not choose a 20 char long password :) my guess would be a just regular chars and like 5-10 chars long. That would not take so long :) Today I helped out a really _really_ paranoid friend of mine ...: [LIST]
[*]we setup complete disk encryption with LUKS (via Ubuntu's "Alternate Install" disk) [INDENT]... LUKS Password length: 16 chars
... the password has a mixture of letters a-z, A-Z, numbers 0-9 and a few special characters {}[]()+"*ç%&! ...[/INDENT]
[*]we setup the ecryptfs-based "Private" folder
[INDENT] ... his user password has 9 chars, same mixture as above [/INDENT]
[*]and to top it off: inside his "Private" folder he uses "encfs" encrypted folders [INDENT] ... 20 chars, again same mixture as above ... [/INDENT]
[/LIST]

so to get to the stuff he really _really_ wants to keep private:
[LIST]
[*]you'd need to break the LUKS password
[*]you'd need to know his user password _OR_ crack the ecryptfs passphrase
[*]you'd then need to crack the "encfs" passphrase for the stuff inside the "Private" folder ... [/LIST]

So I assume he's "safe" ... at least for now? :)

---

