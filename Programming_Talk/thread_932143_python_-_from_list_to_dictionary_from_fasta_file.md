---
title: "python - from list to dictionary from fasta file"
date: 2008-09-28
forum: Programming Talk
---

### Post by slentzen on 2008-09-28
I am trying to solve an exercise where I have to lad a fasta file containing headers starting with >Protein_name, followed by some peoptide sequence.
By using regular expressions, and loops, I have gotten to the point where my list is on the form ['header1','seq1',headern+1',seqn+1']. The list will always have an even number of elements, in the order given above.
Now I should convert the list to a dictionary, where the header files are the keyes, and the respetive sequence strings the values. But I am hitting my head against a wall on how to do this.
Maybe someone can guide me a little on my way towards a solution?

My first idea was to maybe to try with a while loop that first checks that " while list%2 == 0 and len(list)!=0:" the idea that the first part with the modulus operater ensures that the previous formatting has proceeded correctly, and the last part that the loop stops correctly when the extraction is done.

But from there on, I am low on ideas.

Hope anyone here can give me some advice.
Thanks - Slentzen

---

### Post by ad_267 on 2008-09-28
It might be easier if you get your list into a form like this:

```
[['header1','seq1'],[headern+1',seqn+1']]
```

Or just read the data straight into a dictionary.

Or with your list you could use something like:
```

for (i,header) in enumerate(list):
    if i % 2 == 0:
        dictionary[header] = list[i+1]

```

---

### Post by chronographer on 2008-09-28
if you have an even number of entries... maybe you could go

```

for i in range( len ( yourLIst / 2 ):
    pointer = i * 2
    yourDictionary[ yourList( pointer ) ] = yourlist( pointer + 1 )

```
but the best way is to read them directly into list.

See here: [http://docs.python.org/tut/node7.html#SECTION007500000000000000000](http://docs.python.org/tut/node7.html#SECTION007500000000000000000)

---

### Post by Wybiral on 2008-09-28
How about this?

```

data = ['header1', 'seq1', 'headern+1', 'seqn+1']
zipped = zip(data[:-1:2], data[1::2])
mapped = dict(zipped)

```

---

### Post by ad_267 on 2008-09-29
> **Wybiral said:**
> How about this?

That's a pretty nice way to do it. :D

---

