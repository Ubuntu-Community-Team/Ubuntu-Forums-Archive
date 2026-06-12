---
title: "Restarting a C program"
date: 2006-03-07
forum: Programming Talk
---

### Post by Ubuntuud on 2006-03-07
Hi, I'm new to C and I'm trying to write a program to help me learn my words for german/french/latin/greek/english (:)). I would like to have the following structure:

main()
{
  string question1 = What am I eating now?;
  string answer1 = Chocolat;
  string question2 = What am I eating now?;
  string answer2 = Chocolat;
  string guess;

  printf("%s \n", question1);
  scanf("%s", &guess);
  if (guess != answer1)
  {
    printf("Wrong answer \n");
    _Restart program_

How do I do this? Thanks in advance.

---

### Post by lovebyte on 2006-03-07
I guess your question is about loops.  The best thing you can do is get a good C programming textbook and check the chapter about loops (while, do and for loops).

Basically, your code should be something like this:

do {
  printf(...)
  scanf(...)
}while (ANSWER IS NOT CORRECT)

---

### Post by Ubuntuud on 2006-03-07
I know something (nearly invisible) about loops, but I wondered if there was another way. I'll try to do it with a loop now... Thanks.

---

### Post by mostwanted on 2006-03-07
[QUOTE=Ubuntuud]I know something (nearly invisible) about loops, but I wondered if there was another way. I'll try to do it with a loop now... Thanks.[/QUOTE]

goto :)

---

