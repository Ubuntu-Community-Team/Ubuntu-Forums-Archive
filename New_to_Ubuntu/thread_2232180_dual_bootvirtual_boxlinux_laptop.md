---
title: "dual boot/virtual box/linux laptop?"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by jt358 on 2014-06-30
Hi Everyone, hope you won't mind the question.

I'm doing a PhD and have to use the programme STACKS (cresko) + others for analysing genetic data.

I've had a bit of a muckaround using Ubuntu on a USB, but now need to start understanding linux properly.

I have three options it seems (may be wrong)

1. dual booting
2. Use virtual box on my windows laptop
3. Get a laptop with Linix installed

This genetic analysis is the major part of my genetic analysis.

SO.......are options 1/2 above appropriate or would I be better off getting a dedicated Linux laptop. If answer 3, could someone advise on what basic system spec I might need.

Many thanks to you all

---

### Post by sudodus on 2014-06-30
If the computer has a lot of horsepower and memory, installing Ubuntu in a virtual machine is a good idea. Otherwise dual booting is better, because the extra layer of the virtual machine needs some horsepower and memory.

The advantage with a virtual machine is that you can run both systems at the same time.

If you tell us the specs of the computer we can give more detailed advice

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

-o-

Before installing a dual boot system you should ***backup*** your whole system or at least all important files, because installing can go wrong.

---

### Post by mastablasta on 2014-06-30
also installing inside vbox guide: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

some overwhelming data to newbies: 
since you do not need the desktop bling you can choose a lighter version such as Xubuntu or Lubuntu... or install only basic version and then add a windows manager. that will keep system resources down a lot in virtual system while at the same time you have some descent graphical interface where you run your program. 

does the program use GPU for calculations or only CPU? if only CPU and you plan to buy Linux laptop then go with something powerful and descent GPU (like intel CPU with intel graphics chip).

since programs in Linux are opensource there is a chance someone compiled the software you need in Windows. in that case you can just stay on Windows.

---

### Post by jt358 on 2014-06-30
Thanks for the responses. I'll forward my specs when home. Wow some interesting info for me to decipher - many thanks both

Some other information that might make sense to you all is contained in the STACKS manual for installation
[h=3]What are the requirements to run Stacks?[/h]Stacks is written in C++ and can be built in any unix-like environment. It relies on  the [OpenMP]("http://openmp.org/wp/") libraries for parallelism, which are  available in [most  compilers]("http://en.wikipedia.org/wiki/OpenMP#Implementations") including GCC version 4.2 or greater. On Apple&#8217;s OS X, despite  shipping GCC 4.2, OpenMP does not seem to be available (although it is available in OS X Server). Stacks can still be compiled with the parallel functions turned off (specify --disable-openmp to  the configure script when building the package).
To use the web-based user interface Stacks relies on the [MySQL]("http://www.mysql.com/downloads/mysql/") database. Stacks programs output  simple, tab-separated values files, however, if one doesn&#8217;t have access to MySQL. In  principle, other databases could be supported, although that support isn&#8217;t currently planned. Although the  web interface relies on a database, the Stacks pipeline does not. The pipeline is fully functional without  the database, however the web interface is highly recommended to help visualize your data, and if building a genetic map, to enable easy manual corrections to the data.
If you plan to use the database, Stack&#8217;s Perl scripts require the [DBD::mysql]("http://search.cpan.org/dist/DBD-mysql/")  module be installed, and similarly, to export data as an Excel spreadsheet the [Spreadsheet::WriteExcel]("http://search.cpan.org/~jmcnamara/Spreadsheet-WriteExcel-2.37/")  module is required. These modules are installable using the [cpan]("http://search.cpan.org/~andk/CPAN-1.9402/lib/CPAN.pm") program that is installed by default with Perl.

'

---

### Post by jt358 on 2014-06-30
This is on amazon for about £300 - would my programmes etc for large data analysis run on this? thanks

HP Ubuntu 255 G1 15.6 inch Laptop (AMD E1-1500 1.48GHz Dual Core Processor, RAM 4 GB, HDD 750 GB, Integrated Radeon HD 7310 Graphics Graphics VGA HDMI , DVD writer,3 x USB 2.0, Ubuntu 12.04 LTS)

· 1.5 GHz Athlon 64 X2
· 4 GB DDR3 SDRAM
· 750 GB Serial ATA-300
· Linux

---

### Post by plucky on 2014-06-30
> **jt358 said:**
> This is on amazon for about £300 - would my programmes etc for large data analysis run on this? thanks

HP Ubuntu 255 G1 15.6 inch Laptop (AMD E1-1500 1.48GHz Dual Core Processor, RAM 4 GB, HDD 750 GB, Integrated Radeon HD 7310 Graphics Graphics VGA HDMI , DVD writer,3 x USB 2.0, Ubuntu 12.04 LTS)

· 1.5 GHz Athlon 64 X2
· 4 GB DDR3 SDRAM
· 750 GB Serial ATA-300
· Linux

See [laptop](http://www.ebuyer.com/620311-hp-255-g1-laptop-with-ubuntu-h6q17ea-abu)

Same laptop cheaper price with 12.04 installed.

Good Luck

---

### Post by sudodus on 2014-06-30
> **jt358 said:**
> This is on amazon for about £300 - would my programmes etc for large data analysis run on this? thanks

HP Ubuntu 255 G1 15.6 inch Laptop (AMD E1-1500 1.48GHz Dual Core Processor, RAM 4 GB, HDD 750 GB, Integrated Radeon HD 7310 Graphics Graphics VGA HDMI , DVD writer,3 x USB 2.0, Ubuntu 12.04 LTS)

· 1.5 GHz Athlon 64 X2
· 4 GB DDR3 SDRAM
· 750 GB Serial ATA-300
· Linux

It is ***not*** a powerful processor. I don't know how big data set you are going to process, but I think you should consider also second-hand computers with more horsepower (more powerful processors). Maybe you can browse the internet to find out what computers other users of the same software are running.

---

### Post by sp40140 on 2014-06-30
Hi, Are you set on Laptop ( portable)? Or desktop is an option?
It looks like VM is out of option. I would suggest against it.
Dual boot will work depending on the horsepower / specs of the machine.
Also, if you get laptop, I suggest you get intel cpu. I have found that AMD cups in laptops tend to overheat. and as you will need cpu power for your analysis, you will be better off with intel cpu. And by same logic if you are going use the machine to its fullest power, I highly advice to get a business class laptop Ex, ThinkPad from Lenovo, EliteBook from HP, Latitude (or precision if you have the budget)from Dell (instead of consumer class) as they tend to be better designed, more reliable and manage heat better. 
And therefore, my first question: if you can use desktop, it will be better option for cpu intensive applications.

Cheers,

---

### Post by sudodus on 2014-06-30
> **sp40140 said:**
> Hi, Are you set on Laptop ( portable)? Or desktop is an option?
It looks like VM is out of option. I would suggest against it.
Dual boot will work depending on the horsepower / specs of the machine.
Also, if you get laptop, I suggest you get intel cpu. I have found that AMD cups in laptops tend to overheat. and as you will need cpu power for your analysis, you will be better off with intel cpu. And by same logic if you are going use the machine to its fullest power, I highly advice to get a business class laptop Ex, ThinkPad from Lenovo, EliteBook from HP, Latitude (or precision if you have the budget)from Dell (instead of consumer class) as they tend to be better designed, more reliable and manage heat better. 
And therefore, my first question: if you can use desktop, it will be better option for cpu intensive applications.

Cheers,

+1

This is a good description of how to select what computer to use for your main task. I can add: a second-hand business class computer is better than a new consumer class computer for the same price.

---

