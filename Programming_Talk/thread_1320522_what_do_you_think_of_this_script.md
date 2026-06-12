---
title: "what do you think of this script?"
date: 2009-11-09
forum: Programming Talk
---

### Post by FLMKane on 2009-11-09
I found the old [Beginner]Programming Challenge pages, and I attempted the second challenge.

[http://ubuntuforums.org/showthread.php?t=881152](http://ubuntuforums.org/showthread.php?t=881152)


```

#!/usr/bin/env python

def get_forum_name():
    while True:
        try:
            forum_name = raw_input('Please enter your forum name: ')
            assert len(forum_name) > 0
            assert len(forum_name) < 20
            assert forum_name[0] != ' '
            return forum_name
        except AssertionError,e:
            print '''Please enter your forum name. Make sure it is less than
20 characters long, and does not have a space at the beginning.'''
            print   

def get_age():
    try:
        age = raw_input('Please enter your age: ')
        age = int(age)
    except ValueError:
        print 'Make sure your input was an integer'
        get_age()
    try:
        assert age>0
        return age
    except AssertionError:
        print 'input realistic age'
        get_age()

def get_uid():
    try:
        uid= raw_input('Please enter your user id: ')
        uid = int(uid)
    except ValueError:
        print 'Make sure your input was an integer'
        get_uid()
    try:
        assert uid > 0
        assert uid <= 999999
	return uid
    except AssertionError:
        print 'Make sure that the input is between 1 and 999999'
        get_uid()

while True:
    forum_name = get_forum_name()
    age = get_age()
    user_id = get_uid()
    print 'You are %s, age %s next year you will be %s, with user id %s, the next user is %s' % ( str(forum_name), str(age), str(age+1) , str(user_id), str(user_id+1) )
    break



```

what do you think?

---

