---
title: "Java Linguistics"
date: 2009-04-02
forum: Programming Talk
---

### Post by coolkid5 on 2009-04-02
I was wondering whether anyone knew of any Java packages with functions similar to [Ruby Linguistics]("http://www.deveiate.org/projects/Linguistics/wiki/English").  I was thinking of making a translator as a final project in my computer science class so I need the ability to find plural forms of words and different tenses of a given verb (English only).  Writing this in Java myself would be a pain, so I would appreciate it if someone knew of anything like this.

---

### Post by HotCupOfJava on 2009-04-02
java.util.Locale

This works with methods from other classes to supply Java with internationalization features. I don't know how far it would go towards translating, but it aids in formatting things like local times, dates, currencies, etc. Also allows for proper display of text (left to right, right to left, etc).

---

### Post by coolkid5 on 2009-04-02
> **HotCupOfJava said:**
> java.util.Locale

This works with methods from other classes to supply Java with internationalization features. I don't know how far it would go towards translating, but it aids in formatting things like local times, dates, currencies, etc. Also allows for proper display of text (left to right, right to left, etc).

That's an interesting class, but not really what I'm looking for.

I'm really need something where I can get different forms of english words (methods like toPlural("penny") or toPresentParticiple("says")).  For instance, the translator would see a present participle in the source language and then find the appropriate English word and then it would simply call toPresentParticiple(word) to find the translation in the target language.  As I said, similar functions are in the Ruby package, Ruby Linguistics, but I haven't been able to find a Java equivalent.

---

### Post by myrtle1908 on 2009-04-02
Maybe this article will help? [http://www.devx.com/semantic/Article/35088](http://www.devx.com/semantic/Article/35088)

---

