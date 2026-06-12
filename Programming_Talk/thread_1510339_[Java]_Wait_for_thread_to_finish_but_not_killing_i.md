---
title: "[Java] Wait for thread to finish but not killing it"
date: 2010-06-15
forum: Programming Talk
---

### Post by SpinningAround on 2010-06-15
Code below will scan a folder, problem is that I don't want an other classes to start using the getters until the executing has finished. Question is how to do this, I can't kill the object since I need to be able to access the getters.

[PHP]
import java.io.File;
import java.util.ArrayList;


public class Scanner extends Thread{
	private ArrayList<String> dirName = new ArrayList<String>(), fileName = new ArrayList<String>();
	private ArrayList<Long> fileModified = new ArrayList<Long>();
	
	public Scanner(File file[]){
		scan(file);
	}
	
	private File[] dir(File file){
		dirName.add( file.getName() );
		return file.listFiles();
	}
	
	private void file(File file){
		fileModified.add( file.lastModified() );
		fileName.add( file.getName() );
	}
	
	private void scan(File fileA[]){
		int fileCount=0;
		for(File file : fileA){
			if(file.isDirectory()){
				scan( dir(file) );
				dirName.add("¥"); //down
			}
			if(file.isFile()){
				file(file);
				fileCount++;
			}
		}
		dirName.add("€"); //up
		dirName.add(Integer.toString(fileCount));
	}
	
	protected String[] getDirName(){
		dirName.trimToSize();
		return (String[]) dirName.toArray();
	}
	
	protected String[] getFileName(){
		fileName.trimToSize();
		return (String[]) fileName.toArray();
	}
	
	protected Long[] getFileModified(){
		fileModified.trimToSize();
		return (Long[]) fileModified.toArray();
	}

}

[/PHP]

---

### Post by Queue29 on 2010-06-15
threadObject.join();

The thread which executes that will wait for that other thread to complete before moving on.

---

### Post by SpinningAround on 2010-06-15
> **Queue29 said:**
> threadObject.join();

The thread which executes that will wait for that other thread to complete before moving on.

Thanks, though join() needed the thread to be killed.

---

### Post by Queue29 on 2010-06-15
Looking at your code this time, I see you are extending Thread but have not overridden the run() method, which means you don't quite comprehend Java threading yet. (Your code isn't actually threaded yet). What part of your Scanner class are you wanting to run in parallel?

---

### Post by SpinningAround on 2010-06-15
> **Queue29 said:**
> Looking at your code this time, I see you are extending Thread but have not overridden the run() method, which means you don't quite comprehend Java threading yet. (Your code isn't actually threaded yet). What part of your Scanner class are you wanting to run in parallel?

I guessed that I needed some method of Thread but not exactly what. The though was for a class to ask Scanner to scan a folder, then will that class wait for Scanner to finish, then start using the getters. Will add run() method, should make it more correct?

---

### Post by Queue29 on 2010-06-15
> **SpinningAround said:**
>  The though was for a class to ask Scanner to scan a folder, then will that class wait for Scanner to finish, then start using the getters.

What you describe here makes no sense to utilize threading. That's your first and foremost problem. I ask you, what do you expect to run in parallel while the Scanner is scanning the folder? All you're going to end up doing is waiting for the scanner to finish scanning (ergo the original question) and then act on that data. That doesn't call for threading!

---

### Post by Some Penguin on 2010-06-15
Suggestions:

1.  Don't extend Thread.  Instead, either:

a) use a Runnable, and create a Thread using that new Runnable.
b) use a Runnable, and a ThreadPoolExecutor (and perhaps using the Future result),
c) use a Callable, and do the same as (b)

2.  Don't call it Scanner.  There's already a built-in class named Scanner.

3.  Threads can die and the objects will survive, IF they aren't available for garbage collection.  Objects != threads.  Killing threads != killing constituent objects.

Incidentally, if you want to learn a fair bit about how to do threading well, consider getting "Java Concurrency in Practice".

---

