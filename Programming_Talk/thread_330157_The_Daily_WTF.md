---
title: "The Daily WTF"
date: 2007-01-02
forum: Programming Talk
---

### Post by Mirrorball on 2007-01-02
Do you read this site? It's both hilarious and sad at the same time. [The Daily WTF.]("http://thedailywtf.com") They claim all stories are based on real facts. Today this code was submitted:
```

  public class Pair
  {
      private Object first;
      private Object second;
      private Object third;

      public Pair() { }
      public Pair( Object first, Object second, Object third )
      {
          this.first  = first;
          this.second  = second;
          this.third  = third;
      }

      public Object getFirst()  { return first; }
      public Object getSecond() { return second; }
      public Object getThird()  { return third; }

      public void setFirst( Object first  )  { this.first  = first; }
      public void setSecond( Object second ) { this.second  = second; }
      public void setThird( Object third  )  { this.third  = third; }
  }

```:rolleyes: A pair of three. And reading the comments is a must.

> My high school gym teacher used to say "line up in pairs of three", but stopped long before I arrived in his class.  My uncles had seen to that.  Years before, they had repeatedly infuriated him by getting their buddies to line up in groups of six when he'd say that.

He never did figure out (or admit to figuring out) why they were lining up in sixes, but at least he stopped saying "pairs of three".  :p

He was also fond of saying, "If it fits the shoe, wear it."  Interesting guy, but not for any intended reasons....> That's not really Enterprisey. In our company, we've implemented a pair that is around 33.33% bigger than this one, and has double the size of standard, non-enterprisey pairs.

---

### Post by maxamillion on 2007-01-02
Brilliant ... simply brilliant, glad to see smart people are writing code to solve simple everyday problems
</digital_sarcasm>

---

### Post by amo-ej1 on 2007-01-03
It's also one of my favorite sites ;)

Following their posts really boosts your self confidence as a programmer ;)

---

### Post by Grey on 2007-01-03
Today's code snippet is really just the result of code creep I think.  The developer probably originally did have a pair, but needed a triplet in some situation somewhere, so added an extra object to the pair, in crunch mode.  I've written some pretty nasty code myself when time is pressing.

After all, when you are in crunch mode, it's often more about getting the job done than making it pretty.

---

### Post by amo-ej1 on 2007-01-03
True, but when you're new on a project, and the first you see is the result of somebody elses 'crunch mode' your first impression is _WTF_ ? ;)


Edit: But it's not all the result of working under time pressure, sometimes it's just incompetence, allow me to illustrate: [http://thedailywtf.com/forums/thread/107635.aspx](http://thedailywtf.com/forums/thread/107635.aspx)

---

### Post by Mirrorball on 2007-01-03
Paula Bean is a legend. But this is one of my favorite WTFs:
[http://thedailywtf.com/forums/thread/74400.aspx](http://thedailywtf.com/forums/thread/74400.aspx)
I love the $5,000 for "optimization and refinement of algorithms."

---

### Post by Wybiral on 2007-01-03
> **Mirrorball said:**
> Paula Bean is a legend. But this is one of my favorite WTFs:
[http://thedailywtf.com/forums/thread/74400.aspx](http://thedailywtf.com/forums/thread/74400.aspx)
I love the $5,000 for "optimization and refinement of algorithms."

lol, I just read that, thats pretty funny.

---

### Post by Mirrorball on 2007-01-03
[http://thedailywtf.com/forums/thread/109402.aspx](http://thedailywtf.com/forums/thread/109402.aspx)
Learn how to find out if *value* is negative: "-" == value.toString().substr(0,1)

---

### Post by Solver on 2007-01-03
> **Mirrorball said:**
> [http://thedailywtf.com/forums/thread/109402.aspx](http://thedailywtf.com/forums/thread/109402.aspx)
Learn how to find out if *value* is negative: "-" == value.toString().substr(0,1)

That one's hillarious. Well, I can understand that there are some simply bad programmers and programmers who don't know how to handle the language, but how one can know how to convert an int to string and find substrings while not knowing how to check for if(value < 0) :D

---

### Post by maddog39 on 2007-01-03
Ahahaha! I just love this site in general. Its frickin' hilarious. I especially loved this image, lmao:

[IMG]http://img.thedailywtf.com/images/200701/pup/ie7wtf.jpg[/IMG]

---

### Post by Hendrixski on 2007-01-03
Wow

That's a pretty funny site. thanks for sharing it.

---

### Post by Mirrorball on 2007-01-03
> **maddog39 said:**
> Ahahaha! I just love this site in general. Its frickin' hilarious. I especially loved this image, lmao:

[IMG]http://img.thedailywtf.com/images/200701/pup/ie7wtf.jpg[/IMG]
I love funny error messages. There was a program that asked the user to "hit the keyboard like a monkey" to generate random data.

---

### Post by Mirrorball on 2007-01-16
Today's WTF. Throws an exception and immediately catches it. ](*,)
```

  /**
   * Insert the method's description here.
   * Creation date: (02/15/00 6:27:04 PM)
   * @param obj java.lang.Object
   * @param buf java.lang.StringBuffer
   */
  protected
  static
  void doWork(Object obj, StringBuffer buf) {
      try {
          String lastTag = "</" + obj.getClass().getName() + ">";
          int position = buf.toString().lastIndexOf( lastTag );
          String description = getDescription( obj );
          buf.insert( position, description );
      }
      catch (Exception e) {
          try {
              throw new Exception("Error inserting description!");
          }
          catch (Exception ex) {
          }
      }
  }

```
[http://thedailywtf.com/Articles/If_At_First_You_Don't_Succeed.aspx]("http://thedailywtf.com/Articles/If_At_First_You_Don%27t_Succeed.aspx")

---

### Post by amo-ej1 on 2007-01-17
*respect* ;)

---

### Post by Grey on 2007-01-17
Ah, you know, it took me a whole day, but I finally get what was going on in the programmer's mind.  He thought that attempting to throw an exception might fail, so he was trying to ensure that it would succeed.

It's still absolutely ridiculous.  But I think it might be something like that.

---

