---
title: "Netbeans doesn't recognize project folder"
date: 2012-11-13
forum: Programming Talk
---

### Post by slickymaster on 2012-11-13
I have several projects made in Netbeans 7.2 installed on Windows XP SP3. Last week I have installed Xubuntu 12.10 in the same machine (in a different partition), and on Xubuntu I also installed Netbeans 7.2. So far nothing went wrong and everything is running smoothly.

Now the problem I'm facing with is that not all the projects I've done in Netbeans on Windows are recognized by Netbeans on Xubuntu, it just doesn't recognize the project folder. Why is this happening, why are some of the projects recognized and others aren't recognized?

Another issue I'm dealing with is that when I click on 'Open Project' in Netbeans on Xubuntu, under the 'Look in' options none of my USB thumb drives appear, but I'm able to work with them in any other application of Xubuntu.

I would much appreciate any help that could cast a light on this two issues I'm dealling with.

---

### Post by Unterseeboot_234 on 2012-11-13
Let me first talk about how I program java. I installed Sun Java into the Ubuntu system so I can compile and run java from the Terminal. For NetBeans I have a JDK1.7_upadatexxx folder in my Home folder. That is also where I installed NetBeans 7.xx. The Home Folder installs are for two reasons: 

[1] I can have multiple NetBeans, e.g. NetBeans for SE, EE and ME. (I like SE the best). 
[2] Installing java into Ubuntu file system creates issues with file permissions.

Some folks like having write/read protected program files. Personally, when I'm sweating code all I want to worry about is code and not files. You MAY have a file permission problem from Windows but java code files are Unicode text files. NOBODY has sodomized Unicode like Microsoft has. Microsoft is not international. Microsoft is localized.

Now, for your thumb drive (and this is not a NetBeans thingy). In NetBeans you 'Open Project'. You navigate all way the up to Root, e.g. '/', then '/media' and in that folder should be the name of your thumb drive.

On Windows7 you can inadvertently change a thumb drive from FAT32 into exFAT. exFAT is totally non-interchangeable with any other OS. When Win7 says to scan and fix errors on a thumb --> YOU SAY NO. FAT32 is the only format that can plug-n-play with other machines including cameras.

Hope that helps.

---

### Post by slickymaster on 2012-11-14
Thanks a lot for you reply. 

Regarding my second question I already had figure it out, but thanks anyway.

Regarding my first question, what you say just don't cast a light in my issue. 

In my case both JDK and Netbeans are installed in Ubuntu system, but that doesn't seems to me to be what is causing it.

Also, after analyzing the files in some of the projects I didn't saw any differences regarding file permissions, between them, so that also doesn't seems to me to be what is causing it.

So, what can it be then? Any more thoughts?

---

### Post by spjackson on 2012-11-14
Are you able to tar up one of the problem project directories and post it?

---

### Post by slickymaster on 2012-11-14
Okay, here it is. Let us hope you'll be able to figure it out.

---

### Post by spjackson on 2012-11-14
I loaded that without any problem into NetBeans 7.0.1 which I installed from the Ubuntu 12.04 repository. nbproject/project.properties has a Windows path for application.splash, but I wouldn't expect that to prevent it loading.

I'm afraid I can't think why it wouldn't be working for you.

---

### Post by slickymaster on 2012-11-14
I'm almost 100% sure that that application.splash windows path has nothing to do with it, but I can assure you that it's driving me completely nuts. I'm way beyond puzzled.

If I can't get a solution, all I have left is to rebuild the project using the same classes.

Thanks anyway, maybe someone else manages to cast a light in this mystery.

---

### Post by slickymaster on 2012-11-15
> **spjackson said:**
> I loaded that without any problem into NetBeans 7.0.1 which I installed from the Ubuntu 12.04 repository. nbproject/project.properties has a Windows path for application.splash, but I wouldn't expect that to prevent it loading.

I'm afraid I can't think why it wouldn't be working for you.

Maybe you could do me a favour. Can you build this project and upload the jar here? The reason I'm asking this, it's because not even my project jar I'm able to run.

---

### Post by spjackson on 2012-11-15
To start with, I don't have org.pushingpixels.substance.api.skin.SubstanceGraphiteLookAndFeel so I can't build it. Also, I thought you had several projects that wouldn't load into NetBeans. Don't you have the jars from when you were developing on XP, and if not, can't you build what you need on XP?

---

### Post by slickymaster on 2012-11-15
Alright, if you don't have Substance Look and Feel, there's no way you'll manage to build it, but that's not important.

And yes, I have the project's jars, obtained from the builds in XP, and in XP I'm able to run them as I'm able to open those projects in Netbeans, also. That's what is bugging me, why the hell everything is right with both the projects and the jars in XP and everything is wrong with them in Xubuntu.

Anyway I'll rewrite those projects again, now in the Netbeans I have in Xubuntu.

I was just trying to understand what could be the reasons causing this strange situation.

If you manage to remember a few more possible causes, please post them.

---

### Post by Unterseeboot_234 on 2012-11-15
I downloaded your project and attempted to open in NetBeans 7.1.2. The project reveals its source code and structures the Project Tree.

What I found is the deep dependencies of pushing.pixels. A Web search finds their org.pushingpixels.graphic etc. And that .jar needs laf-widget and that .jar needs jgoodies and so on and so forth.

I, personally, have a folder of .jars called .jara_libraries and I collect .jar files and save in that folder.

In NetBeans I Open a Project. In the Project tree I Right-click and in the sub-menu goto the bottom 'Properties'. Second item 'Librabries' and Add JARS.

After all the .jars have been linked you can build.

---

### Post by slickymaster on 2012-11-15
So it might just be a problem with the Substance LAF librarie, and it's dependencies.

That would explain it, because the other two projetcs I mentioned, with the same problem, are also designed using that LAF.

I'll rewrite one of the projects from scratch in Xubuntu, just to see the behavior of it, and later on the day will post the result.

Anyway, thank you Unterseeboot_234 and spjackson for your help.

---

### Post by Unterseeboot_234 on 2012-11-15
Look, I do this all the time with the missing libraries. FYI, NetBeans copies over .jar files into your Project but NOT a folder. A library is, I believe, a folder. I loaded your project and Right-click 'Run', which builds the source code. At every stack trace I noted the missing dependencies. Repeating the processing several times I used many googles to locate:

substance-7.0.jar
laf-widget-7.1.jar
trident-7.0.jar
laf-plugin-7.0.jar

In the Project tree, each time the build stopped, I Right-click the project name -> Properties -> [Dialog]-> Libraires -> Add jar. In your case, if you copied over a folder called 'Substance' and linked it the Project is just like the XP version. Because I linked .jars my Build includes the .jars inside the /dist folder.

The program builds and runs. And, it is very beautiful I must tell you. Unknown if I'm missing some funcitonality .jars which would give me Runtime errors. But I do get the GUI. And, the **Project** is not happy because you made a Library called 'Substance'. My Project builds and runs because I linked the .jars.

---

### Post by slickymaster on 2012-11-15
Well, first of all let me thank you for the compliment in your post.

It's strange, because when I build the project, e.g., when I made the jar, under Project Properties -> Build -> Packaging, I selected the '_**Copy Dependent Libraries**_' option. So I assume that the project jar would contain that library, meaning that I assume that the library jar's would be linked.
One other thing, my Substance LAF library is, as you rightly say, a folder, containing three jar files, substance-swingx-6.3.jar, substance-6.3 and trident-6.3.

I'm assuming that you've done the linking in the project's tree in Netbeans, right? My problem is that as it is now, I'm not able to load the project because Netbeans doesn't recognize the project folder.

---

### Post by Unterseeboot_234 on 2012-11-15
This is just an assumption on my part, but java was born on a Unix system and the classpath could include links all over the www. In modern java the links are usually local. We have some kind of kink link from your XP.

On the Ubuntu NetBeans start a new project. Add package 'calc_val_conc'. Add a new class template: 'AutoSelect'. Using a text editor copy and paste the source into the newly created class file. Do the same for CalcValConc, CalcValConcPanel, DataValidator, DateUtils, NumFilter.

If you tell me to, I will .tar the .jars I mentioned and attach. Link those. Right-click CalcValConc.java in the Project tree... Run. That compiles all into binaries. Build Final will include all dependencies.

I'm no good with ANT, but that is where the pros can tweak. BASH and ANT are subjects I need to have done by now, but I'm stupid.

Don't give up. I adore NetBeans over using Eclipse. I'm angry at Oracle for making JavaFX hardware-specific.

I was an online java consultant for java student labs for over 8 years. So, ask away with any questions.

---

### Post by slickymaster on 2012-11-15
Well, finally solve it, by starting a new project in Xubuntu Netbeans. I kept everything the same, not only classes but also the Substance LAF library and it's working perfectly.

The only difference is the in name of the project folder, originally was 'Calculador Validade Concessões' and now I«ve changed it to 'Calculador Validade Concessoes'. Do you think it could be caused by the 'õ' character in project folder name, since java code files are Unicode?

Yes, I agree with you, regarding Oracle, since they are going to stop supporting swing.

Ok, if I need I'll send my questions regarding Java development. Me too, I'm a huge Netbeans fan, more than Eclipes and JDeveloper.

---

