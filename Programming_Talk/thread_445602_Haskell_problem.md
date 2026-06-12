---
title: "Haskell problem"
date: 2007-05-16
forum: Programming Talk
---

### Post by zanga on 2007-05-16
I need to make a write to file filter function that takes the comment tokens from a list and write's it to a file
so I made a function that tells me if it's a comment or not
isComment :: Token -> Bool
isComment (Tok s r c k) = if k /= Comment then False else True

And a function that takes the comment and write's it in a file
writeComments :: [Token]->IO()
writeComments (t@(Tok s r c k) : ts) =
     if isComment t then writeFile "com.txt" (s) 
     else  writeComments (ts
But it only takes the first comment token:(...Help please...

---

