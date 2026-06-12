---
title: "Searchmonkey, all the power of find/grep ease of Beagle"
date: 2006-11-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Toxicity999 on 2006-11-06
Firstly, a description (Which many how to's lack!):

"Linux currently has two leading search methods: 
 * [Beagle]("http://beagle-project.org/") – simple to use, but shows too many matches.
* [Find]("http://www.gnu.org/software/findutils/")/[Grep]("http://www.gnu.org/software/grep/") – hard to use, but provides exact matching.
searchmonkey takes the best features from both. 
It provides a simple to use interface, but has the power of find and grep combined. In addition, the end search result is an easy to browse list of matching files, and matching lines." (From their wiki)


You'll find an Ubuntu based Deb here:
[http://www.getdeb.net/app.php?name=searchmonkey](http://www.getdeb.net/app.php?name=searchmonkey)

That being for Edgy... not sure on Dapper, sorry folks!

Now if you want to be a hardcore hax0r (kidding, duh!) You'll want to compile it yourself! Also note, this is a How to for the most recent *stable* release, as such you'll have to venture into cvs or svn on your  own, which isn't SO hard anyway. :)

Step One: Let the Source be with you
[http://prdownloads.sourceforge.net/searchmonkey/searchmonkey-0.7.1.tar.gz?download](http://prdownloads.sourceforge.net/searchmonkey/searchmonkey-0.7.1.tar.gz?download)

Step Two: Return of the Apt
sudo apt-get install build-essential
Pretty sure that's all you need... If I'm wrong PLEASE correct me.

Step Three: The Intergalactic Tar Monster!
Extract the folder from your tar file, to your desktop or something...

Step Four: Compiler! why have you forsaken meeee?
cd '/home/NAME/Desktop/searchmonkey-0.7.1'
(replace NAME with name, silly.)
./configure
make

Step Five: Get---In---My------FOLDER!
sudo make install

Step Five: Double-Ewe-Tee-Effe?
I know, I know, it looks complicated at first...
You may want to read up on their wiki about usage, they cover it more than you would want me to here, but play around... you can't hurt much searching.

[http://searchmonkey.sourceforge.net/](http://searchmonkey.sourceforge.net/)

Happy Searching!

---

### Post by Rytron on 2010-04-14
Searchmonkey is an excellent tool alright.

---

### Post by anandnz on 2010-05-29
I use ubuntu 9.10 and search monkey which synaptic or aptitude installs is 0.8.1-6. Not sure your experience but my experience of using this version is that system hangs until i close search monkey application. The application itself hangs, 
Is there a limit of searching, cannot i search a whole project not a very big size but may turn up 100s of search results this tool seems to hang. 

I am not sure how to get the latest 2.0.0 version installed .. any advice is much appreciated. 

Cheers

---

### Post by alluringreality on 2010-07-18
There are instructions for installing searchmonkey 2.0.0 on the download page at their site. Download the source and extract the contents. Then install qt-sdk from the repositories, and the Qt Creator that's mentioned should show up in your menu. Anyway it takes a bit to run and when it's done there will be a new searchmonkey file in the folder. As a windows user I thought the build was generally easy because everything could be done with a GUI. 

Edit: I thought the new version took longer to search than the old version, but this may have been a mistake. If I clear the search history on the old version they take about the same amount of time for a new search.

---

