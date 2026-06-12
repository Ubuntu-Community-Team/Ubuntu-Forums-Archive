---
title: "Removing installed program"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by joetait on 2012-01-23
Hi

I installed some software I found online following the guide on the website, found here [http://www.willus.com/k2pdfopt/help/ubuntu.shtml](http://www.willus.com/k2pdfopt/help/ubuntu.shtml)

However, the program is not working properly - when I run it  makes an output file with very few intelligible characters. 

How can I remove any traces of the program, if there are any sure fire ways. I have gone in to the files mentioned in the guide, but can I just search all files for "k2pdfopt" or something?

Thanks

---

### Post by BC59 on 2012-01-23
There is a tool called Synaptic. If you don't have it installed, you can install it through Ubuntu Software center.
From there search for the package you like to remove. Be careful because is a powerful tool and it's easy to make errors.

---

### Post by snowpine on 2012-01-23
Looking at that tutorial, I think this will work:

```
sudo rm /usr/local/bin/k2pdfopt
rm ~/.local/share/applications/k2pdfopt
```

BE VERY CAREFUL with the "rm" command, especially "sudo rm". Use the copy & paste features, and triple-check for typos before pressing Enter. :)

---

### Post by joetait on 2012-01-23
Does synaptics really cover software isn't available through any repository or the software centre. As in, I just downloaded a file and made in executable and tried to run it (as per the instructions, rather than randomly doing this). I didn't think that synaptics would keep track of extra files made by this.

---

### Post by joetait on 2012-01-23
> **snowpine said:**
> Looking at that tutorial, I think this will work:

```
sudo rm /usr/local/bin/k2pdfopt
rm ~/.local/share/applications/k2pdfopt
```

BE VERY CAREFUL with the "rm" command, especially "sudo rm". Use the copy & paste features, and triple-check for typos before pressing Enter. :)

Okay, that's great, I think that is what I have removed manually, didn't know if there would be anything else.

Thanks

---

### Post by snowpine on 2012-01-23
A binary is just like .exe in Windows, deleting the file removes the application from your system.

---

### Post by BC59 on 2012-01-23
> **joetait said:**
> Does synaptics really cover software isn't available through any repository or the software centre. As in, I just downloaded a file and made in executable and tried to run it (as per the instructions, rather than randomly doing this). I didn't think that synaptics would keep track of extra files made by this.

In Synaptic you can find any package installed, no matter how. Check if there is something remaining from the program you installed.

---

### Post by Cheesemill on 2012-01-23
> **BC59 said:**
> In Synaptic you can find any package installed, no matter how.

Not true.

Synaptic only keeps track of .deb files, not packages installed from source or pre-compiled binarys installed via any other method.

---

### Post by BC59 on 2012-01-23
I was meaning the .deb packages of course installed by any source.

---

### Post by Cheesemill on 2012-01-23
> **BC59 said:**
> I was meaning the .deb packages of course installed by any source.

Sorry. You did actually say packages didn't you :)

I was referring to the OP where he described installing a downloaded binary.

---

