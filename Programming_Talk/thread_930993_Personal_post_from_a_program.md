---
title: "Personal post from a program"
date: 2008-09-26
forum: Programming Talk
---

### Post by gomputor on 2008-09-26
[PHP]#!/usr/bin/env python

class PersonalPost(object):
    def __init__(self, post):
        self.post = post

    def __str__(self):
        return self.post

if __name__ == "__main__":
    post = """
              Hello  everybody. This  is  just a
              silly post with no  purpose at all.
              No questions to  be answered  here.
              If you think  that you can write a
              better one, then  I'll be  happy to
              read it. But please  note that I'll
              accept posts only from programs and
              not straight  from  you. Your  post
              can be written in any language. We,
              machines and software, do  not make
              discriminations of  any  kind  that
              you people do  all the time. And of
              course additions or better impleme-
              ntations of our .selves  are always
              welcome  and is  something that  we
              always seek after.
                         Thank you!"""

    my_post = PersonalPost(post)
    print my_post
[/PHP]

---

