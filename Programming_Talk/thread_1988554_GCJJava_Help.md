---
title: "GCJ/Java Help"
date: 2012-05-27
forum: Programming Talk
---

### Post by JBudOne on 2012-05-27
Hey guys!

   Newbie GDB and GCJ user here; I'm very much interested in using these great tools, but I'm having troubles getting it to work. I've looked through the man file, and Googled around, but surprisingly I can't find anything regarding my issue. Really I've just got a simple java file, which also uses a few other java files in the same folder; but my attempt at GCJ fails in each of these cases:

```

gcj --classpath=LinkedList.jar --main=Test Test.java -o Test
gcj --main=Test Test.java -o Test
gcj --main=Test Test.java --classpath=. -o Test
gcj --main=Test Test.java *.class -o Test

```

Each of which result in,

```

/tmp/ccgXmg5a.o: In function `void Test::main(JArray<java::lang::String*>*)':
ccFYJXzD.jar:(.text+0x51): undefined reference to `LinkedList::class$'
ccFYJXzD.jar:(.text+0x60): undefined reference to `LinkedList::LinkedList()'
ccFYJXzD.jar:(.text+0x6f): undefined reference to `ListNode::class$'
ccFYJXzD.jar:(.text+0x90): undefined reference to `ListNode::ListNode(int, ListNode*)'
ccFYJXzD.jar:(.text+0x1cd): undefined reference to `LinkedList* LinkedList::readBigInteger(java::util::Scanner*)'
ccFYJXzD.jar:(.text+0x1fd): undefined reference to `LinkedList* LinkedList::readBigInteger(java::util::Scanner*)'
ccFYJXzD.jar:(.text+0x4ba): undefined reference to `LinkedList* LinkedList::readBigInteger(java::util::Scanner*)'
collect2: ld returned 1 exit status

```

Well I'm completely stumped. Calling `*java -classpath LinkedLi.jar Test*`   works just fine. Any ideas? Tips? Hints? I'd love to get some insight into what's going on here. Thanks guys! :)

---

