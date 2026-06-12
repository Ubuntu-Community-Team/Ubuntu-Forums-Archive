---
title: "Phyton loop issue with twitter client?"
date: 2011-07-11
forum: Programming Talk
---

### Post by mikedemon on 2011-07-11
hjgh
kl
l

---

### Post by Zugzwang on 2011-07-11
Please write your code in "[CODE]"-tags. In your case this is rather important because the cause of your problem might be improper indentation, which we will only see if you put your code into the TAGS, as otherwise, the indentation is not preserved.

---

### Post by mikedemon on 2011-07-11
Hi
 
Code does work but doesnt get the details of each user from twitter , brings up the detials of the last user from the text file.

---

### Post by cgroza on 2011-07-11
We still need that code with the right indentation. Without indentation we are unable to interpret your program properly.
Please repost your code inside code tags.

---

### Post by mikedemon on 2011-07-11
```

 
csvfile.close()
 
 

```

---

### Post by TwoEars on 2011-07-11
> **mikedemon said:**
> ```

 
import csv, math, time
import twitter as twitterapi
 
api = twitterapi.Api(consumer_key='xxxxxxxxxxxx', 
consumer_secret='xxxxxxxxxxx', 
access_token_key='xxxxxx-xxxxxx', 
access_token_secret='xxxxxxxxxxxxxxxxxxx')
 
listofnames = file('twit.txt').readlines()
listofnames = [name.strip() for name in listofnames]
 
csvfile=open('twittercounts.csv','ab')
csvout=csv.writer(csvfile,dialect='exc…
 
for name in listofnames:
account = api.GetUser(name)
followers = account.followers_count
csvout.writerow([name, followers])
print name + ", " + str(followers)
csvfile.close()
 
 

```

Well, let me tell you this now, that program won't run. 
```
for name in listofnames:
```
tells the interpretor to look for an indent. You haven't provided one, so you will meet - ```
IndentationError: expected an indented block
```
Unless, of course, you've wrapped this program in a naive and foolish, like - 
```

try: 
    code
except:
    #Catch every exception here
    pass

```

My guess is that you've actually done the for-loop incorrectly, so you have something like this - 
```

for name in listofnames:
    account = api.GetUser(name)
    followers = account.followers_count
csvout.writerow([name, followers])
print name + ", " + str(followers)
csvfile.close()

```
See the problem?
If not, try this and see if you can work it out - 
```

for x in xrange(3):
    print 'Value of x during loop: %d' % x

print 'Value of x after loop: %d' % x

```

---

