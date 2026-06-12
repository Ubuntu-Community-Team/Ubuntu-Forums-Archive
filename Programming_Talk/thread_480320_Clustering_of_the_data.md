---
title: "Clustering of the data"
date: 2007-06-21
forum: Programming Talk
---

### Post by anuraggautam on 2007-06-21
Hi Everybody !
   I am working on Clustering of the data.I have database of the dictionary including Antonyms and Synonyms.
I have to detect the sense and throw a output for the relevant words [ you can say including the Antonyms].
please tell me how to cluster the data so that it can be more efficient and it can throw more relevant words.

For expamles : if i put the input " Hotel"
         it can throw      "public house, resort, roadhouse, rooming house, scratch crib, spa, tavern"

like more near to these words....

Please help me to find the good algorithm.

Regards,

---

### Post by Lux Perpetua on 2007-06-21
Are you just implementing a thesaurus?

You can start with a map whose keys are words and whose values are lists of synonyms (or antonyms). Many popular languages already have built-in map and multimap types (like C++), so you might not even need to think about the algorithm, but in the background, there is almost certainly a balanced tree or hash table.

---

