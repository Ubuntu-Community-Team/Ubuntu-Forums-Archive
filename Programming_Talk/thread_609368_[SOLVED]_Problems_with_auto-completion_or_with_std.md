---
title: "[SOLVED] Problems with auto-completion or with stdlib ?"
date: 2007-11-10
forum: Programming Talk
---

### Post by lefredbleu on 2007-11-10
Hi,

I tried 3 different IDE (geany, netbeans, and Code::blocks) for C++ coding.  I always get this problem with auto-completion and error correction: IDE does not seem to recognize C++ standard libraries (ex.  netbeans write me an error when I write #include <string> and does not give me options after I write std:: or someString. ; same problem with other IDE).  It is not just a problem with auto-completion, since it works with my custom headers.  It seems that stdlib headers are not recognized.  

Libraries are there, and in the end, programs compile correctly despite the "errors" that are shown by the IDEs.  Still, as I am learning C++, being given a list of standard classes, or std classes methods with some comment is very useful to me (ex.  I always forget if it is someString.empty() or someString.isEmpty()).

If you know what might be the source of this problem, please help me.

ps.  I have ubuntu supported libstdc++, with doc and dev installed, so this is not the problem.

---

### Post by nrs on 2007-11-10
While I cannot help since I don't use these IDEs, usually there is an option hidden somewhere to parse/index libraries you've included. Try searching for either Parser or Indexer in the menus. 

I'm sorry I don't know the proper non-Microsoft-marketing term, Eclipse is the only *nix IDE I know of that supports decent "Intellisense". I think there is a 3rd party proprietary emacs addon suite that costs a couple of hundred dollars, I forget its name.

---

### Post by LaRoza on 2007-11-10
> **nrs said:**
> 
I'm sorry I don't know the proper non-Microsoft-marketing term, Eclipse is the only *nix IDE I know of that supports decent "Intellisense". 

Code Completion

It is very common and the MS name was just for marketing.

---

### Post by nrs on 2007-11-10
> **LaRoza said:**
> Code Completion

It is very common and the MS name was just for marketing.

I'm sure there is a more specific term. Code Completion is too vague, and can range anywhere from simple auto-complete to something more complex (though still simple), like limiting the available completions based on the object or namespace it's being called from, etc.

---

### Post by LaRoza on 2007-11-10
> **nrs said:**
> I'm sure there is a more specific term. Code Completion is too vague, and can range anywhere from simple auto-complete to something more complex (though still simple), like limiting the available completions based on the object or namespace it's being called from, etc.

I never experienced this MS feature, and I don't use IDE's, so I am not familiar with the various implementations, but others who have used it said it was code completion.

---

### Post by lefredbleu on 2007-11-11
I didn't know auto-completion was a MS marketing word.  I often see "auto-completion" being used when people talk about netbeans code completion too.

I guess this is the problem.  Parser/Indexer probably don't see stdlib by default.  I'll try it and come back

---

### Post by LaRoza on 2007-11-11
> **lefredbleu said:**
> I didn't know auto-completion was a MS marketing word.  I often see "auto-completion" being used when people talk about netbeans code completion too.


No, Intellisense is.

---

### Post by lefredbleu on 2007-11-11
I tried it with eclipse and it works.  So it is a netbeans problem...  I think this now belong to a netbeans specific forum.  Thanks for the help, I'll mark it as closed since it is netbeans related and nobody seems to use it.

---

