---
title: "Python regex; operations within found range of text"
date: 2013-08-23
forum: Programming Talk
---

### Post by kumoshk on 2013-08-23
I'm using regular expressions within Python.

What I'm wanting to do is find all the text between two special characters (it could be pages) and then perform a second separate regular expression only on that text in that location. Is there a way to do this?

I'm guessing findall() is kind of what I need for finding it, but once I find that text and perform the operations, how do I put it back into my document with the changes, without making things complicated? (Or even if it is kind of complicated.)

Right now, my solution without that is to loop through the novel, finding things with count=1, changing to put a special identifier there, and continuing looping through in some nested fashion that is kind of hard to wrap one's head around. So, if we could do what I'm asking above, that would be great.

Maybe there's some separate non-regex function to find the text, but I'm not sure how to do that and operate on it afterward. Let me know your thoughts.

Thanks!

More specifically what I'm doing is deciding whether or not to put line breaks at the end of each line where a cluster of text matches certain criteria (but the same document will have clusters with line breaks and without&#8212;however, I don't want each line to be examined; I want each cluster to be examined and then all the line breaks within the cluster to be either added or not).

---

### Post by ofnuts on 2013-08-23
I think you should use finditer() for the outer loop, so that you get MatchObject that will also tell you the start/end indexes for the match. Then you process the matched string and replace it in the source using the positions.

---

