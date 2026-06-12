---
title: "unit testing with phpunit how to?"
date: 2011-07-22
forum: Programming Talk
---

### Post by iansane on 2011-07-22
Hi,

I have been trying to figure out how to use the phpunit package to perform TDD like with junit.

So far I have found 3 different versions all claiming to be the real phpunit. (Ubuntu repository version, pear channel version, and one on sourceforge written by a different author than the one in the pear channel). All 3 versions have slightly different files. For instance the Ubuntu version does not have phpunit.php which is required to follow directions here [http://pear.php.net/manual/en/package.php.phpunit.intro.php](http://pear.php.net/manual/en/package.php.phpunit.intro.php)

The pear version is lacking the /util/CodeCoverage.php which is included in the Ubuntu version and required for use with phpunitwebui from sourceforge here [http://sourceforge.net/projects/phpunitwebui/](http://sourceforge.net/projects/phpunitwebui/)

I would love to get phpunitwebui working and for the most part it is, once I get the paths set up in the config file. The graphical representation is so much better than using command line in my opinion and it works by actually dropping the Ubuntu version into my www directory rather than having to rely on something being installed on the server. 

The problem with the webui version is that I get a fatal error message ( PHPUnit_Framework_TestSuite not found on line 441 of functions.php) so I look at that line and right above it is
```
require_once 'testSuite.php';
```
but it is commented out.

I un-comment the line and get another error. (fatal error can not re declare class) referring to the following line in the testSuite.php file
```
class PHPUnit_Framework_TestSuite implements PHPUnit_Framework_Test, PHPUnit_Framework_SelfDescribing, IteratorAggregate{//there's a lot of code here but I think it is the definition of the class in general that is causing the error}
```

It seems like the class has already been defined somewhere else.

I looked through all included and required scripts, used find and grep to search the entire directory for the class, and installed and ran xdebug and nowhere can I find where that class has already been defined.

So I have two important questions.

1. Can anyone point me to a tutorial specifically for the Ubuntu version of phpunit?

2. Would someone with more coding knowlege like to assist me in getting the phpunitwebui version working with the Ubuntu version of phpunit?

Thank you very much for any assistance with either but I would prefer to get the webui version working.

---

### Post by iansane on 2011-07-22
unbelievable! I decided to take a look at simpletest [http://www.simpletest.org/](http://www.simpletest.org/) thinking by the name it would be a much more simplified process and have more web designer oriented features which it does. So I decide to check synaptic to see if there is a repository version to install and there is. It's called php-simpletest.

And what happens when I go to the getting started tutorial at simpletest to learn how to use it? The same thing that happened with phpunit. First thing, a file that is required part of using simpletest the way it's creators intended it to be used is missing from the Ubuntu version.

What is the deal with Ubuntu feeling the need to mess with and re-write things like this? It's just a folder full of php files so it's not like it has to be changed to work on Ubuntu and it definately doesn't need to be compiled into a installation package. Pulling my hair out with frustration at this!

When someone goes to the trouble of making a good tutorial with simple examples you should not make changes to it without including a revised tutorial of the same high quality that tells people how to use your version of it.

---

