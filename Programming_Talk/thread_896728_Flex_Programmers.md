---
title: "Flex Programmers"
date: 2008-08-21
forum: Programming Talk
---

### Post by Felson on 2008-08-21
I am in the process of converting a bunch of Flash programs to Flex since I don't want to have to have in Winblows box here at work just for 1 small aspect of my job. Plus, with Flex, I can put it on the server and do my work from anywhere I want. 

I was wondering though, how many of us [UKX]buntu programmers use flex at all? How you like it as compared to Flash CS*? What kind of things you are using it for? If you have found any good ways to reduce the binary size?



To kick it off, so far I like Flex better. That may just be because I have never really been a fan of Wysiwyg IDEs. I find I can do my job faster in plain text once I understand the language and syntax. At the moment I have only made calculators with it, though I will need to make a FLV player and an image slide show as well.

---

### Post by SeanHodges on 2008-08-22
Flex developer here.

I can't compare it to Flash CS, as I've never used it. I imagine they are reasonably similar fundamentally, but it might be worth running through a few basic Flex tutorials to make sure you're up to speed.

In case you haven't found it already, the SDK is here:

[http://labs.adobe.com/technologies/flex/sdk/](http://labs.adobe.com/technologies/flex/sdk/)

One thing I did need to do is modify one of the scripts in the SDK to work correctly with Ant, if you don't use Ant for building your projects you hopefully won't need to do this: [http://labs.adobe.com/wiki/index.php/Talk:Flex_Ant_Tasks#Problem_with_compc_task_on_linux_.28.27unknown_configuration_variable_compiler.source-path.27.29](http://labs.adobe.com/wiki/index.php/Talk:Flex_Ant_Tasks#Problem_with_compc_task_on_linux_.28.27unknown_configuration_variable_compiler.source-path.27.29)


Beyond the Flex SDK (which can be extracted anywhere), you can use pretty much any cross-language tools you are use to already (Eclipse/Gedit/Vim/Emacs/Ant/Automake...)

There is a Flex Builder plugin for Eclipse, which gives you syntax highlighting, auto-completion, etc. The only drawback is that the Linux version is currently in early alpha development, which most importantly means it does not have a design view (which is available in the Windows version). Once it is functionally complete it will be a pay-for product just like the Windows one, but for now you can download the alpha version and get some of the features for free:

[http://labs.adobe.com/technologies/flex/flexbuilder_linux/](http://labs.adobe.com/technologies/flex/flexbuilder_linux/)

Thats about all I can think of for now... Except to bear in mind there are 2 major Flash players in the Linux world, Adobe's Flash player and Gnash. If you develop against one, be sure to test with the other occasionally.

---

### Post by aloshbennett on 2008-08-22
One major difference is the change from timeline movie based approach from flash to the ajax oriented approach in flex.

---

