---
title: "Linking the Synaptic's JMagick to ImageMagick"
date: 2011-11-17
forum: Programming Talk
---

### Post by Unterseeboot_234 on 2011-11-17
Hello,
I used Synaptic to install everything JMagick and ImageMagick. JMagick requires the JNI link from my Java Project to ImageMagick. I can't seem to find what the link or sym-link should be.

Anybody have any success setting up JMagick to a java project? Most of my searching shows Ubuntu 9.10 solutions with a svn ./configure with a lot of path variables. I would think the Synaptic version would have all that done already.

---

### Post by Unterseeboot_234 on 2011-11-17
After spending a lot of time with this failure, I wanted to tell what does work first.
In regular JavaSE you can hand off a String[] arr to
```
    private static boolean exec(String[] command) {
        Process proc;

        try {
            System.out.println("Trying to execute command " + Arrays.asList(command));
            proc = Runtime.getRuntime().exec(command);
        } catch (IOException e) {
            System.out.println("IOException while trying to execute " + command);
            return false;
        }
```

With JNI you wouldn't end up with a portable software application. JNI is invariably such a nightmare unless you install a complete API, SDK, and then build JMagick with a lot of flags set so to connect java to native. IMHO, Synaptic libjmagick could not match the user's JDK with the ImageMagick version. Ubuntu loves to rename the libs to stave off OS cracks. JMagick has slowed development since a couple of years backwards.

Anyway, if you find this thread, try Runtime.getRuntime().exec( myIMcmmd )

---

