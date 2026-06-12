---
title: "how to combine two if statements"
date: 2013-04-14
forum: Programming Talk
---

### Post by Aeons Midgard on 2013-04-14
if (timedSyllables.size() > 0) {
                        if (timedSyllables.get(0).getMilliSeconds() <= nowMs) {
                            timedHighlightText = timedSyllables.get(0)
                                    .getSyllable().trim();
                            if( !timedHighlightText.equals( MainConstants.STRINDEXFILENEWLINE ) && !timedHighlightText.equals( MainConstants.STRBLANK )) {
                                System.out.println(":::" + timedHighlightText + ":::" + timedSyllables.get(0).getMilliSeconds() + " : " + nowMs);
                                lyricsHandler.sendEmptyMessage(2);
                            }
                            timedSyllables.remove(0);
                            
                            System.gc();
                        }
                    }


                     if (lyricsLines.size() > 0) {
                         if ( lyricsLines.get(0).getMicroSeconds() <= elapsedMs ) {
                             strLine = lyricsLines.get(0).getPhrase();
                             System.out.println("Line :::" + strLine + ":::" + (lyricsLines.get(0).getMicroSeconds()) + " : " + nowMs);
                             lyricsHandler.sendEmptyMessage(1);
                             lyricsLines.remove(0);
                             System.gc();
                         }
                     }

---

### Post by Bucky Ball on 2013-04-15
*Thread moved to **Programming Talk**.*

---

### Post by r-senior on 2013-04-15
The title of the post suggests that you have two if statements that you would like to combine, but then the body of the post shows some Java code with five if statements?

Is it just that you want to transform:

```
if (A) {
    if (B) {
        doSomething();
    }
}
```

into:

```
if (A && B) {
    doSomething();
}
```

Or is it something else? Perhaps you could explain what you would like to do?

Could you also wrap any code that you post in [noparse]```
...
```[/noparse] tags so that it keeps its indentation?

And why are you calling System.gc()?

---

### Post by fr0s7y on 2013-04-15
Could you not use an IF ELSE statement?

```
if (lyricsLines.size() > 0) {
                         
                     } else if ( lyricsLines.get(0).getMicroSeconds() <= elapsedMs ) {
                             strLine = lyricsLines.get(0).getPhrase();
                             System.out.println("Line :::" + strLine +  ":::" + (lyricsLines.get(0).getMicroSeconds()) + " : " + nowMs);
                             lyricsHandler.sendEmptyMessage(1);
                             lyricsLines.remove(0);
                             System.gc();
                         }
```

---

### Post by slickymaster on 2013-04-15
> **r-senior said:**
> 
```
if (A && B) {
    doSomething();
}
```
+1 on r-senior's suggestion.

> **r-senior said:**
> And why are you calling System.gc()?
Again, I'm compelled to agree with r-senior.
Why are you calling it? You don't know what sort of garbage collector you are running under. Some JVMs aren't that smart or for various reasons don't do it. You don't know what it's going to do. Also, it's not guaranteed to do anything. The JVM may just entirely ignore your request.
Sometimes people suggest that calling gc() may return memory to the system. That's certainly not necessarily true - the Java heap itself grows independently of Java allocations.
As in, the JVM will hold memory and grow the heap as necessary. It doesn't necessarily return that memory to the system even when you free Java objects; it is perfectly free to hold on to the allocated memory to use for future Java allocations.

---

### Post by ofnuts on 2013-04-15
> **r-senior said:**
> And why are you calling System.gc()?

Voodoo programming...  either you call the garbage collector or you gut a chicken in front of the servers rack. Both are about as efficient but the OP either has signed the PETA chart (Programmers for the Empirical Treatment of Animals) or wants to remain in good terms with the cleaning personnel.

---

