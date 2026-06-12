---
title: "Facebook Hidden Friends list trouble."
date: 2014-11-22
forum: Programming Talk
---

### Post by george85 on 2014-11-22
I have very limited knowledge with Terminal in Ubuntu, I'm wondering if you can help me :)


I'm trying to access my friend's 'Hidden Friend' list with this code by Shay Priel mentioned here (bottom of the page), running Ubuntu on VirtualBox (virtual machine). 


I'd like to mention that this code is not "hacking", it's using the Facebook API to it's full potential. Nothing criminal going on here…


[http://lifehacker.com/uncover-every-friend-on-someone-s-private-facebook-frie-1586250899](http://lifehacker.com/uncover-every-friend-on-someone-s-private-facebook-frie-1586250899)


The code is uploaded here. [https://github.com/prili/fb-hfc](https://github.com/prili/fb-hfc)


and I've installed the pre-requisite items, using sudo command. All installed successfully.


apt-get install python-lxml
pip install selenium
pip install requests
pip install colorama


When I use this command in terminal to run the script.
~/Desktop/fb-hfc.py -username <inserted my username here> -password <inserted my password here> -query ‘People who live in Los Angeles California and like SBE’ -output related_profiles.txt


it throws this error. What does this mean? 


Traceback (most recent call last):
  File "/home/george/Desktop/fb-hfc.py", line 301, in <module>
    graph_search(graph_search_query)
  File "/home/george/Desktop/fb-hfc.py", line 117, in graph_search
    elem.click()
  File "/usr/local/lib/python2.7/dist-packages/selenium/webdriver/remote/webelement.py", line 65, in click
    self._execute(Command.CLICK_ELEMENT)
  File "/usr/local/lib/python2.7/dist-packages/selenium/webdriver/remote/webelement.py", line 385, in _execute
    return self._parent.execute(command, params)
  File "/usr/local/lib/python2.7/dist-packages/selenium/webdriver/remote/webdriver.py", line 173, in execute
    self.error_handler.check_response(response)
  File "/usr/local/lib/python2.7/dist-packages/selenium/webdriver/remote/errorhandler.py", line 166, in check_response
    raise exception_class(message, screen, stacktrace)
selenium.common.exceptions.MoveTargetOutOfBoundsException: Message: Element cannot be scrolled into view:[object XrayWrapper [object HTMLDivElement]]
Stacktrace:
    at WebElement.clickElement (file:///tmp/tmpEw3Vlq/extensions/fxdriver@http://googlecode.com/components/command-processor.js:11036:7)
    at DelayedCommand.prototype.executeInternal_/h (file:///tmp/tmpEw3Vlq/extensions/fxdriver@http://googlecode.com/components/command-processor.js:11635:16)
    at DelayedCommand.prototype.executeInternal_ (file:///tmp/tmpEw3Vlq/extensions/fxdriver@http://googlecode.com/components/command-processor.js:11640:7)
    at DelayedCommand.prototype.execute/< (file:///tmp/tmpEw3Vlq/extensions/fxdriver@http://googlecode.com/components/command-processor.js:11582:5)
george@george-VirtualBox:~$ ~/Desktop/fb-hfc.py

---

### Post by komppa97 on 2015-07-19
This thread is few months old but I still found it :P
I've got exactly same problem , hopefully somebody could help us!

> Traceback (most recent call last):  File "fb-hfc.py", line 301, in <module>
    graph_search(graph_search_query)
  File "fb-hfc.py", line 116, in graph_search
    elem = driver.find_element_by_xpath("//div[@class='_586i']")
  File "/usr/local/lib/python2.7/dist-packages/selenium-2.46.0-py2.7.egg/seleniu                                                                                                                     m/webdriver/remote/webdriver.py", line 252, in find_element_by_xpath
    return self.find_element(by=By.XPATH, value=xpath)
  File "/usr/local/lib/python2.7/dist-packages/selenium-2.46.0-py2.7.egg/seleniu                                                                                                                     m/webdriver/remote/webdriver.py", line 684, in find_element
    {'using': by, 'value': value})['value']
  File "/usr/local/lib/python2.7/dist-packages/selenium-2.46.0-py2.7.egg/seleniu                                                                                                                     m/webdriver/remote/webdriver.py", line 195, in execute
    self.error_handler.check_response(response)
  File "/usr/local/lib/python2.7/dist-packages/selenium-2.46.0-py2.7.egg/seleniu                                                                                                                     m/webdriver/remote/errorhandler.py", line 170, in check_response
    raise exception_class(message, screen, stacktrace)
selenium.common.exceptions.NoSuchElementException: Message: Unable to locate ele                                                                                                                     ment: {"method":"xpath","selector":"//div[@class='_586i']"}
Stacktrace:
    at FirefoxDriver.prototype.findElementInternal_ (file:///tmp/tmpsXzkAs/exten                                                                                                                     sions/fxdriver@googlecode.com/components/driver-component.js:10299)
    at fxdriver.Timer.prototype.setTimeout/<.notify (file:///tmp/tmpsXzkAs/exten                                                                                                                     sions/fxdriver@googlecode.com/components/driver-component.js:603)

---

