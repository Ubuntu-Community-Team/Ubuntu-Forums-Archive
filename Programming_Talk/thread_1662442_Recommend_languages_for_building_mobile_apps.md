---
title: "Recommend languages for building mobile apps?"
date: 2011-01-08
forum: Programming Talk
---

### Post by linuxforartists on 2011-01-08
I'm currently studying web design, and I'm curious about how mobile apps are developed. What are the main languages coders use for doing that?

On a related note, is it easier to develop for iPhone or Android?

---

### Post by unknownPoster on 2011-01-08
Android apps are programmed in a dialect of Java, IPhone apps are  programmed in Objective-C. In order to actually put your apps on an  Iphone, you will need a modern Apple computer.

---

### Post by Lootbox on 2011-01-08
It's probably easier to get started developing for the Android. To develop an iPhone app, you need to have an Apple computer. In order to deploy the app to an actual device, you have to pay a fee. The Android SDK is available on multiple platforms (including Linux), and is free of charge.

As for the actual coding, I don't have experience with Objective-C. The Java that the Android platform uses is "Java" only in syntax; it's an entire platform of its own, and can take some time to learn.

---

### Post by linuxforartists on 2011-01-09
Thanks for the advice, unknownPoster and Lootbox.  Looks like Android is the way to go.

---

### Post by kalaharix on 2011-01-09
Android development is an immature market. Other solutions will come.

There is already a very interesting basic4android under Windows ([www.basic4ppc.com](www.basic4ppc.com)). There is a 30day trial with (very slow) onscreen emulation.

---

### Post by eeperson on 2011-01-09
> **kalaharix said:**
> Android development is an immature market. Other solutions will come.

There is already a very interesting basic4android under Windows ([www.basic4ppc.com](www.basic4ppc.com)). There is a 30day trial with (very slow) onscreen emulation.

This brings up a good point.  You can actually do Android development with any language that will run on the JVM.  I actually prefer [Scala]("http://www.scala-lang.org/") for Android development.  It is much more expressive than Java while still being just as performant.  You can find directions on how to use it [here]("http://www.assembla.com/wiki/show/scala-ide/Developing_for_Android").

---

### Post by linuxforartists on 2011-01-10
> **eeperson said:**
>  I actually prefer [Scala]("http://www.scala-lang.org/") for Android development.  It is much more expressive than Java while still being just as performant.  You can find directions on how to use it [here]("http://www.assembla.com/wiki/show/scala-ide/Developing_for_Android").

If I'm not mistaken, didn't Twitter switch away from Ruby on Rails to use Scala?  That's a vote of confidence.  Thanks for that link.

---

### Post by eeperson on 2011-01-10
> **linuxforartists said:**
> If I'm not mistaken, didn't Twitter switch away from Ruby on Rails to use Scala?  That's a vote of confidence.  Thanks for that link.

They switched their back end processing to Scala.  I believe they are still doing their UI in with Rails.  Foursquare and LinkedIn are done all in Scala.

---

### Post by johnaaronrose on 2011-12-13
Has anyone tried installing/using Basic4Android under Ubuntu or using Wine on Ubuntu? If so, can yoy offer any advice on setting it up for development?

---

### Post by imagecko on 2011-12-14
You can write apps in Actionscript in Flash too.

---

### Post by 11jmb on 2011-12-14
> **eeperson said:**
> This brings up a good point.  You can actually do Android development with any language that will run on the JVM. 

Be careful here. Dalvik != JVM.

There are many ways for you to develop Android apps in other languages (if you have a compelling reason to do so)

sl4a will allow you to use your favorite scripting language when writing Android apps.

ndk will allow you to compile C/C++ projects for your app to run

I haven't done any Scala on Android, but IIRC, you have to bundle the Scala library with every single app, because Android does not support runtime linking. (Don't stone me if this is false or outdated, though)

---

