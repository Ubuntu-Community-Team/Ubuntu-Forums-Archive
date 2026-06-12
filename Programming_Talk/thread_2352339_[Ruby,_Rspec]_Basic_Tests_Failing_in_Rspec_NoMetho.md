---
title: "[Ruby, Rspec] Basic Tests Failing in Rspec: NoMethodError"
date: 2017-02-11
forum: Programming Talk
---

### Post by Meowcenary on 2017-02-11
[FONT=verdana]I'm working on a small project in Ruby and using Rspec to write my tests. Normally I do not have any problems with the initial steps of my test driven process, but today when I created an empty function in my class and was testing for the existence of this method I received a NoMethodError. I had previously verified that the files were being loaded properly and the described class does match the class I have written. I'm not sure why it is not recognizing the method and would appreciate any help in determining this. [/FONT][FONT=verdana]I have also tested the class in it's own file by instantiating the class at the bottom of the file and then calling the method to verify that it was indeed a part of the class and returning the proper value. Which has led me to think something has gone wrong with Rspec.
[/FONT]
[FONT=verdana]Please read the comment on the gist provided. It explains how my files are organized since I did not know how to create sub directories in gist.
Here is the code: [https://gist.github.com/Meowcenary/c9a26cdc539b1a23a5f20bfc468f3183](https://gist.github.com/Meowcenary/c9a26cdc539b1a23a5f20bfc468f3183)[/FONT]
[FONT=verdana]
**Working on a Windows 10 machine using Bash on Ubuntu on Windows as my terminal

Edit: [/FONT][FONT=verdana]I've changed the code so that I instantiate the class instead of using described_class and that seems to work. I'm going to dig into this some more, but it seems odd I can't just call the method on described_class.
Edit2: I think the proper way to do this is to use "subject" for each group and then testing on that. I'm going to consider this problem solved now and it can be deleted if it is deemed unhelpful to anyone else.[/FONT]

---

