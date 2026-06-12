---
title: "Problem with code completion in Netbeans php plugin in Xubuntu 9.04"
date: 2009-05-09
forum: Programming Talk
---

### Post by riden on 2009-05-09
Hi folks,

I have Xubuntu 9.04 amd64 clean installation, then I do
```

$ sudo apt-get install sun-java6-jdk
$ sudo apt-get install netbeans

```for installing Sun JDK 1.6u13 and Netbeans 6.5 from ubuntu repositories. Seems it works well, but it comes only with a few modules. PHP module is missing. I go to *Tools -> Plugins*, select *Available plugins* tab, type 'php' in search, check *PHP* module in results and then click *Install* button. Things are going well: plugin is installed, I can create a PHP project, create a files. The one bad thing is that code completion is not work properly and also I see error message in Netbeans status bar:
```

Annotation: Root: /home/riden/NetBeansProjects/PhpProject1 File: index.php Bootpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/riden/.netbeans/6.5/phpstubs/phpruntime/]] Classpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/riden/.netbeans/6.5/phpstubs/phpruntime/]] Sourcepath: ClassPath[Entry[file:/home/riden/NetBeansProjects/PhpProject1/]]
Annotation: Root: /home/riden/NetBeansProjects/PhpProject1 File: index.php Bootpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/riden/.netbeans/6.5/phpstubs/phpruntime/]] Classpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/riden/.netbeans/6.5/phpstubs/phpruntime/]] Sourcepath: ClassPath[Entry[file:/home/riden/NetBeansProjects/PhpProject1/]]
Root: /home/riden/NetBeansProjects/PhpProject1 File: index.php Bootpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/riden/.netbeans/6.5/phpstubs/phpruntime/]] Classpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/riden/.netbeans/6.5/phpstubs/phpruntime/]] Sourcepath: ClassPath[Entry[file:/home/riden/NetBeansProjects/PhpProject1/]]
Root: /home/riden/NetBeansProjects/PhpProject1 File: index.php Bootpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/riden/.netbeans/6.5/phpstubs/phpruntime/]] Classpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/riden/.netbeans/6.5/phpstubs/phpruntime/]] Sourcepath: ClassPath[Entry[file:/home/riden/NetBeansProjects/PhpProject1/]]
Caused: java.lang.RuntimeException: Can't find cluster
    at org.netbeans.modules.php.editor.index.PHPIndex.getClusterUrl(PHPIndex.java:317)
    at org.netbeans.modules.php.editor.index.PHPIndex.getPreindexUrl(PHPIndex.java:285)
    at org.netbeans.modules.php.editor.index.PHPIndexer.getPersistentUrl(PHPIndexer.java:196)
    at org.netbeans.modules.gsfret.source.usages.CachingIndexer$LanguageIndex.index(CachingIndexer.java:171)
    at org.netbeans.modules.gsfret.source.usages.CachingIndexer.index(CachingIndexer.java:118)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater.batchCompile(RepositoryUpdater.java:2031)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker.updateFolder(RepositoryUpdater.java:1404)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker.scanRoots(RepositoryUpdater.java:1129)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker.access$1900(RepositoryUpdater.java:651)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker$1.run(RepositoryUpdater.java:838)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker$1.run(RepositoryUpdater.java:679)
    at org.netbeans.modules.gsfret.source.usages.ClassIndexManager.writeLock(ClassIndexManager.java:107)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker.run(RepositoryUpdater.java:676)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker.run(RepositoryUpdater.java:651)
    at org.netbeans.napi.gsfret.source.Source$CompilationJob.run(Source.java:1347)
    at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:441)
    at java.util.concurrent.FutureTask$Sync.innerRun(FutureTask.java:303)
    at java.util.concurrent.FutureTask.run(FutureTask.java:138)
    at java.util.concurrent.ThreadPoolExecutor$Worker.runTask(ThreadPoolExecutor.java:886)
    at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:908)
[catch] at java.lang.Thread.run(Thread.java:619)

```This error comes when PHP project is loaded.

I can guess that there are missed depenidencies and seems I am right. I install minimalistic Netbeans 6.5 on Windows for only PHP development, found the list of installed plugins and install essential for my view in my Xubuntu installation. They are *Editing files* and *Web client tools*. After installation I see the positive changes :) Code completion works better with two exceptions:
- it does not work inside any class definition (neither reserved words nor functions and class members);
- it does not work with class members at any point of code.
And I also see error, but of another nature:
```

java.lang.ArrayIndexOutOfBoundsException: 0
    at org.netbeans.modules.php.editor.index.PHPIndex.getTypeSpecificSignatures(PHPIndex.java:608)
    at org.netbeans.modules.php.editor.index.PHPIndex.getMethods(PHPIndex.java:529)
    at org.netbeans.modules.php.editor.index.PHPIndex.getAllMethods(PHPIndex.java:385)
    at org.netbeans.modules.php.editor.PHPCodeCompletion.autoCompleteClassMembers(PHPCodeCompletion.java:858)
    at org.netbeans.modules.php.editor.PHPCodeCompletion.complete(PHPCodeCompletion.java:264)
    at org.netbeans.modules.gsfret.editor.completion.GsfCompletionProvider$JavaCompletionQuery.addCodeCompletionItems(GsfCompletionProvider.java:589)
    at org.netbeans.modules.gsfret.editor.completion.GsfCompletionProvider$JavaCompletionQuery.resolveCompletion(GsfCompletionProvider.java:575)
    at org.netbeans.modules.gsfret.editor.completion.GsfCompletionProvider$JavaCompletionQuery.run(GsfCompletionProvider.java:405)
    at org.netbeans.modules.gsfret.editor.completion.GsfCompletionProvider$JavaCompletionQuery.run(GsfCompletionProvider.java:233)
    at org.netbeans.napi.gsfret.source.Source.runUserActionTask(Source.java:485)
    at org.netbeans.modules.gsfret.editor.completion.GsfCompletionProvider$JavaCompletionQuery.query(GsfCompletionProvider.java:307)
    at org.netbeans.spi.editor.completion.support.AsyncCompletionTask.run(Unknown Source)
    at org.openide.util.RequestProcessor$Task.run(Unknown Source)
[catch] at org.openide.util.RequestProcessor$Processor.run(Unknown Source)

```And this error comes when I press Ctrl+Space for completion.

Then I install all modules that I found in windows minimalistic installation. And as I expect, it is without changes.

There are no problems with bundled Sun Netbeans package.

Does somebody have the same error?

---

### Post by cartman_ on 2009-05-10
Hi,

the same happens to me as well on Ubuntu 9.04 64b :(

```
Annotation: Root: /var/www/epi_portal File: CaseInsensitive.php Bootpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/cartman/.netbeans/6.5/phpstubs/phpruntime/]] Classpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/cartman/.netbeans/6.5/phpstubs/phpruntime/]] Sourcepath: ClassPath[Entry[file:/var/www/epi_portal/]]
Annotation: Root: /var/www/epi_portal File: CaseInsensitive.php Bootpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/cartman/.netbeans/6.5/phpstubs/phpruntime/]] Classpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/cartman/.netbeans/6.5/phpstubs/phpruntime/]] Sourcepath: ClassPath[Entry[file:/var/www/epi_portal/]]
Root: /var/www/epi_portal File: CaseInsensitive.php Bootpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/cartman/.netbeans/6.5/phpstubs/phpruntime/]] Classpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/cartman/.netbeans/6.5/phpstubs/phpruntime/]] Sourcepath: ClassPath[Entry[file:/var/www/epi_portal/]]
Root: /var/www/epi_portal File: CaseInsensitive.php Bootpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/cartman/.netbeans/6.5/phpstubs/phpruntime/]] Classpath: ClassPath[Entry[nbfs://nbhost/SystemFileSystem/PHP/RuntimeLibraries/], Entry[file:/home/cartman/.netbeans/6.5/phpstubs/phpruntime/]] Sourcepath: ClassPath[Entry[file:/var/www/epi_portal/]]
Caused: java.lang.RuntimeException: Can't find cluster
    at org.netbeans.modules.php.editor.index.PHPIndex.getClusterUrl(PHPIndex.java:317)
    at org.netbeans.modules.php.editor.index.PHPIndex.getPreindexUrl(PHPIndex.java:285)
    at org.netbeans.modules.php.editor.index.PHPIndexer.getPersistentUrl(PHPIndexer.java:196)
    at org.netbeans.modules.gsfret.source.usages.CachingIndexer$LanguageIndex.index(CachingIndexer.java:171)
    at org.netbeans.modules.gsfret.source.usages.CachingIndexer.index(CachingIndexer.java:118)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater.batchCompile(RepositoryUpdater.java:2031)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker.updateFolder(RepositoryUpdater.java:1404)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker.scanRoots(RepositoryUpdater.java:1129)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker.access$1900(RepositoryUpdater.java:651)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker$1.run(RepositoryUpdater.java:789)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker$1.run(RepositoryUpdater.java:679)
    at org.netbeans.modules.gsfret.source.usages.ClassIndexManager.writeLock(ClassIndexManager.java:107)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker.run(RepositoryUpdater.java:676)
    at org.netbeans.modules.gsfret.source.usages.RepositoryUpdater$CompileWorker.run(RepositoryUpdater.java:651)
    at org.netbeans.napi.gsfret.source.Source$CompilationJob.run(Source.java:1347)
    at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:471)
    at java.util.concurrent.FutureTask$Sync.innerRun(FutureTask.java:334)
    at java.util.concurrent.FutureTask.run(FutureTask.java:166)
    at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1110)
    at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:603)
[catch] at java.lang.Thread.run(Thread.java:636)
```

---

### Post by cl333r on 2009-05-10
Folks don't bother, get NetBeans from their site, it
a) works fine
b) current version is already 6.5.1

[http://www.netbeans.org/downloads/](http://www.netbeans.org/downloads/)

---

### Post by riden on 2009-05-10
**cl333r**, thanks for advice, I tried the bundled version from Netbeans site (6.5.1) and it worked well. The main idea that I want to satisfy is to save (x)ubuntu integrity. This means that all software I want to install should come in and come out using packages. So, I think I need to create a custom package from bundled Netbeans version and install it using local folder as repository until I know the reason of described problem and how to fix it.

Up: I just create a custom deb package from a Sun bundled.

---

