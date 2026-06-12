---
title: "Installing a software from Java Projects"
date: 2014-03-29
forum: Programming Talk
---

### Post by tolga2 on 2014-03-29
Hello, what I would like to achieve is installing a software from java application that I created. I've got permission with gksudo. Then, I typed my pass and the program started working until yes/no option was appeared. How can I pass this question ? 



```
installation =Runtime.getRuntime().exec(new String[]{"gksudo","apt-get","install","PACKAGE"});
```
```
inputSw = new BufferedReader(new InputStreamReader(installation.getInputStream()));
```

```
while( (lineSw=inputSw.readLine())!=null) 
 {
                        
   System.out.println(lineSw); 
  }

```

---

### Post by oldos2er on 2014-03-29
Moved to Programming Talk.

---

### Post by Erik1984 on 2014-03-30
You could try this option in the apt-get command:

```

       -y, --yes, --assume-yes
           Automatic yes to prompts; assume "yes" as answer to all prompts and
           run non-interactively. If an undesirable situation, such as
           changing a held package, trying to install a unauthenticated
           package or removing an essential package occurs then apt-get will
           abort. Configuration Item: APT::Get::Assume-Yes.

```

---

