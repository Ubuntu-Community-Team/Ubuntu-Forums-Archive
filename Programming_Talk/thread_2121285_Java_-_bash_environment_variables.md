---
title: "Java - bash environment variables"
date: 2013-03-01
forum: Programming Talk
---

### Post by yellowzelo on 2013-03-01
Hi folks,

there are certain bash environment variables defined in my *~/.bashrc* and accessing them through bash terminal works indeed. But these environment variables are not accessible when I try to execute any command in Java.

For example, when I run following code:

```

    try {
        //run command "printenv"
        Process proc = Runtime.getRuntime().exec("printenv");
        BufferedReader read = new BufferedReader(new InputStreamReader(proc.getInputStream()));

        //print output
        while (read.ready())
            System.out.println(read.readLine());
        
    } catch (IOException e) {
            System.out.println(e.getMessage());
    }

```


it does not print all environment variables (excludes those defines in *~/.bashrc*). But running command *printenv* directly in bash terminal prints all environment variables.

One of the options is pharsing ~/.bashrc in Java to read environment variables. Are there any other options?


Thank you for your help.

---

### Post by slickymaster on 2013-03-01
IMHO, parsing is a very good option. Just output the environment variables and in your Java parser simply read one line at a time and split on the first equals sign on each line. You could store them in a Map, where the bit before the equals sign would be the key, and the bit after it would be the value, i.e. **VAR_NAME=VAR_VALUE** would become **<VAR_NAME, VAR_VALUE>** in a Map<String, String>.

---

### Post by r-senior on 2013-03-01
It's not a good option if someone wants to run it who doesn't have a .bashrc file though. Could you define the values you need in a .properties file? No need to parse that, just load up with the load() method of Java.util.Properties. You could also load it from the classpath with getResourceAsStream() from java.lang.Class.

Edit: Alternatively, have you tried System.getenv() to get environment variables?

---

### Post by slickymaster on 2013-03-01
> **r-senior said:**
> It's not a good option if someone wants to run it who doesn't have a .bashrc file though.
To be honest that scenario didn't cross my mind.
> **r-senior said:**
> Edit: Alternatively, have you tried System.getenv() to get environment variables?
Yes, good idea. It's really much simpler than parsing, plus it's still possible to store them the some way I previously posted:
```
Map<String, String> env = System.getenv();
for (String envName : env.keySet()) {
     System.out.format("%s=%s%n", envName, env.get(envName));
}
```

---

### Post by ofnuts on 2013-03-01
IMHO, Bash is Bash and Java is Java. Your Java code should really use System.getProperty(), and the bash script that starts the Java app could define theses properties from environment variables:
```

java -Dsome.property=$SOME_BASH_VARIABLE YourApp

```

---

