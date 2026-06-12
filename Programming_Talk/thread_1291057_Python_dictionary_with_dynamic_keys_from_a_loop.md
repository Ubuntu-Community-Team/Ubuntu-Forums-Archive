---
title: "Python dictionary with dynamic keys from a loop"
date: 2009-10-14
forum: Programming Talk
---

### Post by mbeach on 2009-10-14
Still relatively new to python, and still running into things I know must have a better way.

I'm populating a dictionary by looping over a queryset to effectively sum  quiz scores and group by student. 
The queryset has records like
Student, topic, score
where one (student,topic) pairing can have many scores
s1, t1, 98
s1, t1, 86
s2, t1, 92
s2, t2, 88

That resulting dictionary looks like:
scores[student][topic] = aggregate

Then to make the django template which displays the data easier to deal with, I'm creating a list of dictionary which looks like
```

scoreslist = []
for student in scores:
  scoreslist.append({'student':student,
                     'topic1':scores[student]['t1'],
                     'topic2':scores[student]['t2'],
                      .
                      .
                      .
                     'topicn':scores[student]['tn'],
                    })

```
Where 'n' is some arbitrary number. Right now it is hardwired in at 10, but I want the flexibility of having a loop inside of that append to any number I pass into the method dealing with this. 

What I think I need is some way to do this :
```

scoreslist = []
for student in scores:
  scoreslist.append({'student':student,
                      (topic.name:scores[student][topic.name] for topic in topiclist),
                    })

```


Eventually, that template displays the data with the student names down the left as row headers, and the topics across the top as column headers.

Also, and not quite as appropriate for this particular forum is in the template how to subsequently be able to not have to do:
```

{% for st in studentscores %}
<td>{{ st.topic1 }}</td>
<td>{{ st.topic2 }}</td>
<td>{{ st.topic3 }}</td>
<td>{{ st.topic4 }}</td>
.
.
.

```
How does one have an inner loop there in a django template where the "topic1" "topic2" are dynamic. How would you loop over the topics list. Pass it in as a separate context but then how to loop over it passing the values as keys to the outer loop? I cannot get something like the following to work:
```

{% for st in studentscores %}
  {% for t in topic %}
    <td>{{ st.t }}</td>
  {% endfor %}
{% endfor %}

```

Small disclaimer, this is all being done on Google App Engine, so django 0.96 mostly for template stuff - using webapp otherwise (valuelist does not appear to be an option)

---

### Post by mbeach on 2009-10-14
funny how having to explain it all sometimes helps you see the answer.

Apparently this bit works just fine - I had my syntax all wrong.
```

for s in scores:
  scorelist.append([scores[s][t] for t in topics])

```

---

