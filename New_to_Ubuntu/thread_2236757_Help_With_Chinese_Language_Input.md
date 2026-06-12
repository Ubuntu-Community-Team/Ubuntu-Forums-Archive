---
title: "Help With Chinese Language Input"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by colin23 on 2014-07-28
Hello, I am running Ubuntu from a DVD to see if I would like to switch to it. Being totally unfamiliar with the OS, apart from what little I've picked up since last night, I have very little knowledge of how to make things work.

My primary language is English, but I absolutely *must* be able to type in simplified Chinese characters, because I am learning Chinese for school. This is a big enough deal that if I can't resolve this issue I will have to give up on the idea of using Ubuntu.

So, I clicked the "En" button at the top right. There, I found some options for different language inputs. I selected Chinese - pinyin.

I can't figure out how to make it work, though. It seems to not recognize more than two letters at a time for one character, but the pinyin for many, if not most, characters is three letters. This is a major problem.

When I have it switched on and try to type a three letter character, it registers the first two letters as one character and treats the third letter as the initial of a new character.

For example, the word hao gets split into ha-o. Like this: &#21704;o. Hen gets split into he-n, like this: &#21644;n

How can I get Ubuntu to recognize more than two letters as pinyin for a single character?

For what it's worth, I'm used to being able to write in Chinese on both Windows and on my iPhone, and neither have given me any major problems, and never anything like this.

Thanks for any help!

---

### Post by grahammechanical on 2014-07-28
May i suggest something? Setting up an additional keyboard layout is one thing. You now need to set up Chinese language support. We do that in System Settings>Language Support. When the utility opens Click Install/Remove languages. Then after you have installed Chinese look at the panel labelled Keyboard Input Method System. The default is Ibus but with Chinese language support added you may get an additional option.

There is another way that you might be interested in. Ubuntu Kaylin.

[http://www.ubuntu.com/desktop/ubuntu-kylin](http://www.ubuntu.com/desktop/ubuntu-kylin)

And add an English keyboard layout and English language support to that flavour of Ubuntu.

Regards.

---

### Post by colin23 on 2014-07-28
Thank you for your advice. Unfortunately, it didn't change anything because I already had simplified Chinese installed. It is able to display the characters, but I can't figure out how to make it work for typing when the pinyin is more than two letters per character.

I would be willing to try Kaylin, but I have only had one year of learning Chinese so far, and I'm afraid I would have too much difficulty setting it up.

---

### Post by monkeybrain20122 on 2014-07-28
I have set up fctix for someone on 13.10. This repo works for 14.04 [https://launchpad.net/~fcitx-team/+archive/ubuntu/dailybuild-fcitx-master](https://launchpad.net/~fcitx-team/+archive/ubuntu/dailybuild-fcitx-master)

ibus seems to be quite broken and fctix is recommended by many as a better option. It is used in Kylin as default.

---

### Post by colin23 on 2014-07-29
I'll be perfectly honest. I don't know what exactly I did, but between fiddling around with the settings and restarting my computer two or three times, I managed to get it working just fine. This was on the 32-bit Ubuntu 14.04 LTS on my old junk computer. I installed the 64-bit on my main computer this afternoon, and again had problems, and again fixed it through some magic combination of not knowing what I'm doing and rebooting a few times.

I can't explain it, but it's taken care of for the time being. Thanks a lot for the help, guys. I'll make sure to try to find this thread again if something starts giving me problems again at a later date.

&#35874;&#35874; &#65307;&#65289;

---

