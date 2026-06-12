---
title: "bash: ./interproscan.sh: No such file or directory"
date: 2015-08-18
forum: New to Ubuntu
---

### Post by mirza3 on 2015-08-18
Hello everyone,

I have downloaded and installed Interproscan interproscan-5.14-53.0 in my ubantu system. I have 
 1. java version "1.6.0_35" OpenJDK Runtime Environment (IcedTea6 1.13.7) (6b35-1.13.7-1ubuntu0.12.04.2) OpenJDK 64-Bit Server VM (build 23.25-b01, mixed mode) 
2. perl 5, version 14, subversion 2 (v5.14.2) built for x86_64-linux-gnu-thread-multi (with 57 registered patches 
3. Python 2.7.3
When i am trying to run the software, even for a test file it returns
"bash: ./interproscan.sh: No such file or directory"

please help me out!

---

### Post by steeldriver on 2015-08-18
Did you check the md5 sum before unpacking the archive? 

Are you sure you are running the command from the correct directory? what is the output of 

```

ls -l

```

in the terminal where you are trying to run the command?

---

### Post by mirza3 on 2015-08-19
Yes, I did check the md5 sum as recommended and the results were ok.
I am running the command from the correct directory and the output of  ls -l
total 716
drwxrwxr-x 16 smarla smarla   4096 Jul 24 17:49 bin
drwxrwxr-x 16 smarla smarla   4096 Aug 18 13:53 data
-rwxrwxr-x  1 smarla smarla 424788 Jul 24 17:49 interproscan-5.jar
-rw-rw-r--  1 smarla smarla  10300 Jul 24 17:49 interproscan.properties
-rwxrwxr-x  1 smarla smarla   1176 Jul 24 17:49 interproscan.sh
drwxrwxr-x  2 smarla smarla  12288 Jul 24 17:51 lib
-rw-rw-r--  1 smarla smarla    158 Jul 24 17:49 readme.txt
drwxrwxr-x  3 smarla smarla   4096 Jul 24 17:49 src
-rw-rw-r--  1 smarla smarla   1498 Jul 24 17:51 test_all_appl.fasta
-rw-rw-r--  1 smarla smarla  97649 Jul 24 17:49 test_convert_mode.xml
-rw-rw-r--  1 smarla smarla   6582 Jul 24 17:49 test_nt_redundant.fasta
-rw-rw-r--  1 smarla smarla  95414 Jul 24 17:49 test_nt_seqs_convert_mode.xml
-rw-rw-r--  1 smarla smarla   5396 Jul 24 17:49 test_nt_seqs.fasta
-rw-rw-r--  1 smarla smarla  18596 Jul 24 17:49 test_proteins_convert_mode.xml
-rw-rw-r--  1 smarla smarla   1685 Jul 24 17:49 test_proteins.fasta
-rwxrwxr-x  1 smarla smarla   1649 Jul 24 17:49 test_proteins_new.fasta
-rwxrwxr-x  1 smarla smarla   4259 Jul 24 17:51 test_proteins_redundant.fasta
-rw-rw-r--  1 smarla smarla    272 Jul 24 17:49 test_single_protein.fasta
drwxrwxr-x  3 smarla smarla   4096 Jul 24 17:49 work

---

### Post by nerdtron on 2015-08-19
```
 -rwxrwxr-x  1 smarla smarla   1176 Jul 24 17:49 interproscan.sh 
```

Here is your interproscan.sh file. Are you trying to run this command? Just try ./interproscan.sh or "bash interproscan.sh". Post your  complete output here if you have errors.

---

### Post by mirza3 on 2015-08-19
Its running now, thank you so much.

---

### Post by mirza3 on 2015-08-19
The given Test file (test_proteins.fasta) runs successfully. However, when I try to run my data file (as small as containing only 3-4 sequences, in fasta format), interproscan fails.
Instead of, 100% done:  InterProScan analyses completed
I get,
19/08/2015 14:28:28:357 Welcome to InterProScan-5.14-53.0
19/08/2015 14:28:36:902 Running InterProScan v5 in STANDALONE mode...
Loading file /home/smarla/my_interproscan/interproscan-5.14-53.0/sng_ara_pro_1.fasta
19/08/2015 14:28:41:798 Running the following analyses:
[jobProDom-2006.1,jobHAMAP,jobSMART-6.2,jobSuperFamily-1.75,jobPRINTS-42.0,jobPanther-9.0,jobGene3d-3.5.0,jobPIRSF-3.01,jobPfam,jobPrositeProfiles,jobTIGRFAM-15.0,jobPrositePatterns,jobCoils-2.2]
Available matches will be retrieved from the pre-calculated match lookup service.

Matches for any sequences that are not represented in the lookup service will be calculated locally.
19/08/2015 14:29:40:461 26% completed
2015-08-19 14:30:33,268 [uk.ac.ebi.interpro.scan.jms.worker.LocalJobQueueListener:192] ERROR - Execution thrown when attempting to executeInTransaction the StepExecution.  All database activity rolled back.
java.lang.ArrayIndexOutOfBoundsException: 10
	at uk.ac.ebi.interpro.scan.io.match.prints.PrintsMatchParser.parse(PrintsMatchParser.java:78)
	at uk.ac.ebi.interpro.scan.management.model.implementations.prints.ParsePrintsOutputStep.execute(ParsePrintsOutputStep.java:74)
	at uk.ac.ebi.interpro.scan.jms.activemq.StepExecutionTransactionImpl.executeInTransaction(StepExecutionTransactionImpl.java:86)
	at sun.reflect.GeneratedMethodAccessor65.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:622)
	at org.springframework.aop.support.AopUtils.invokeJoinpointUsingReflection(AopUtils.java:319)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.invokeJoinpoint(ReflectiveMethodInvocation.java:183)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:150)
	at org.springframework.transaction.interceptor.TransactionInterceptor.invoke(TransactionInterceptor.java:110)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:172)
	at org.springframework.aop.framework.JdkDynamicAopProxy.invoke(JdkDynamicAopProxy.java:202)
	at com.sun.proxy.$Proxy95.executeInTransaction(Unknown Source)
	at uk.ac.ebi.interpro.scan.jms.worker.LocalJobQueueListener.onMessage(LocalJobQueueListener.java:180)
	at org.springframework.jms.listener.AbstractMessageListenerContainer.doInvokeListener(AbstractMessageListenerContainer.java:562)
	at org.springframework.jms.listener.AbstractMessageListenerContainer.invokeListener(AbstractMessageListenerContainer.java:500)
	at org.springframework.jms.listener.AbstractMessageListenerContainer.doExecuteListener(AbstractMessageListenerContainer.java:468)
	at org.springframework.jms.listener.AbstractPollingMessageListenerContainer.doReceiveAndExecute(AbstractPollingMessageListenerContainer.java:326)
	at org.springframework.jms.listener.AbstractPollingMessageListenerContainer.receiveAndExecute(AbstractPollingMessageListenerContainer.java:264)
	at org.springframework.jms.listener.DefaultMessageListenerContainer$AsyncMessageListenerInvoker.invokeListener(DefaultMessageListenerContainer.java:1071)
	at org.springframework.jms.listener.DefaultMessageListenerContainer$AsyncMessageListenerInvoker.executeOngoingLoop(DefaultMessageListenerContainer.java:1063)
	at org.springframework.jms.listener.DefaultMessageListenerContainer$AsyncMessageListenerInvoker.run(DefaultMessageListenerContainer.java:960)
	at java.lang.Thread.run(Thread.java:701)
2015-08-19 14:30:33,372 [uk.ac.ebi.interpro.scan.jms.master.StandaloneBlackBoxMaster:58] WARN - StepInstance 41 is being re-run following a failure.
19/08/2015 14:30:33:433 52% completed
2015-08-19 14:30:43,440 [uk.ac.ebi.interpro.scan.jms.worker.LocalJobQueueListener:192] ERROR - Execution thrown when attempting to executeInTransaction the StepExecution.  All database activity rolled back.
java.lang.ArrayIndexOutOfBoundsException: 10
	at uk.ac.ebi.interpro.scan.io.match.prints.PrintsMatchParser.parse(PrintsMatchParser.java:78)
	at uk.ac.ebi.interpro.scan.management.model.implementations.prints.ParsePrintsOutputStep.execute(ParsePrintsOutputStep.java:74)
	at uk.ac.ebi.interpro.scan.jms.activemq.StepExecutionTransactionImpl.executeInTransaction(StepExecutionTransactionImpl.java:86)
	at sun.reflect.GeneratedMethodAccessor65.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:622)
	at org.springframework.aop.support.AopUtils.invokeJoinpointUsingReflection(AopUtils.java:319)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.invokeJoinpoint(ReflectiveMethodInvocation.java:183)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:150)
	at org.springframework.transaction.interceptor.TransactionInterceptor.invoke(TransactionInterceptor.java:110)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:172)
	at org.springframework.aop.framework.JdkDynamicAopProxy.invoke(JdkDynamicAopProxy.java:202)
	at com.sun.proxy.$Proxy95.executeInTransaction(Unknown Source)
	at uk.ac.ebi.interpro.scan.jms.worker.LocalJobQueueListener.onMessage(LocalJobQueueListener.java:180)
	at org.springframework.jms.listener.AbstractMessageListenerContainer.doInvokeListener(AbstractMessageListenerContainer.java:562)
	at org.springframework.jms.listener.AbstractMessageListenerContainer.invokeListener(AbstractMessageListenerContainer.java:500)
	at org.springframework.jms.listener.AbstractMessageListenerContainer.doExecuteListener(AbstractMessageListenerContainer.java:468)
	at org.springframework.jms.listener.AbstractPollingMessageListenerContainer.doReceiveAndExecute(AbstractPollingMessageListenerContainer.java:326)
	at org.springframework.jms.listener.AbstractPollingMessageListenerContainer.receiveAndExecute(AbstractPollingMessageListenerContainer.java:264)
	at org.springframework.jms.listener.DefaultMessageListenerContainer$AsyncMessageListenerInvoker.invokeListener(DefaultMessageListenerContainer.java:1071)
	at org.springframework.jms.listener.DefaultMessageListenerContainer$AsyncMessageListenerInvoker.executeOngoingLoop(DefaultMessageListenerContainer.java:1063)
	at org.springframework.jms.listener.DefaultMessageListenerContainer$AsyncMessageListenerInvoker.run(DefaultMessageListenerContainer.java:960)
	at java.lang.Thread.run(Thread.java:701)
2015-08-19 14:30:43,539 [uk.ac.ebi.interpro.scan.jms.master.StandaloneBlackBoxMaster:58] WARN - StepInstance 41 is being re-run following a failure.
19/08/2015 14:30:43:587 80% completed
2015-08-19 14:30:48,547 [uk.ac.ebi.interpro.scan.jms.worker.LocalJobQueueListener:192] ERROR - Execution thrown when attempting to executeInTransaction the StepExecution.  All database activity rolled back.
java.lang.ArrayIndexOutOfBoundsException: 10
	at uk.ac.ebi.interpro.scan.io.match.prints.PrintsMatchParser.parse(PrintsMatchParser.java:78)
	at uk.ac.ebi.interpro.scan.management.model.implementations.prints.ParsePrintsOutputStep.execute(ParsePrintsOutputStep.java:74)
	at uk.ac.ebi.interpro.scan.jms.activemq.StepExecutionTransactionImpl.executeInTransaction(StepExecutionTransactionImpl.java:86)
	at sun.reflect.GeneratedMethodAccessor65.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:622)
	at org.springframework.aop.support.AopUtils.invokeJoinpointUsingReflection(AopUtils.java:319)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.invokeJoinpoint(ReflectiveMethodInvocation.java:183)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:150)
	at org.springframework.transaction.interceptor.TransactionInterceptor.invoke(TransactionInterceptor.java:110)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:172)
	at org.springframework.aop.framework.JdkDynamicAopProxy.invoke(JdkDynamicAopProxy.java:202)
	at com.sun.proxy.$Proxy95.executeInTransaction(Unknown Source)
	at uk.ac.ebi.interpro.scan.jms.worker.LocalJobQueueListener.onMessage(LocalJobQueueListener.java:180)
	at org.springframework.jms.listener.AbstractMessageListenerContainer.doInvokeListener(AbstractMessageListenerContainer.java:562)
	at org.springframework.jms.listener.AbstractMessageListenerContainer.invokeListener(AbstractMessageListenerContainer.java:500)
	at org.springframework.jms.listener.AbstractMessageListenerContainer.doExecuteListener(AbstractMessageListenerContainer.java:468)
	at org.springframework.jms.listener.AbstractPollingMessageListenerContainer.doReceiveAndExecute(AbstractPollingMessageListenerContainer.java:326)
	at org.springframework.jms.listener.AbstractPollingMessageListenerContainer.receiveAndExecute(AbstractPollingMessageListenerContainer.java:264)
	at org.springframework.jms.listener.DefaultMessageListenerContainer$AsyncMessageListenerInvoker.invokeListener(DefaultMessageListenerContainer.java:1071)
	at org.springframework.jms.listener.DefaultMessageListenerContainer$AsyncMessageListenerInvoker.executeOngoingLoop(DefaultMessageListenerContainer.java:1063)
	at org.springframework.jms.listener.DefaultMessageListenerContainer$AsyncMessageListenerInvoker.run(DefaultMessageListenerContainer.java:960)
	at java.lang.Thread.run(Thread.java:701)
2015-08-19 14:30:48,652 [uk.ac.ebi.interpro.scan.jms.activemq.NonZeroExitOnUnrecoverableError:24] FATAL - Analysis step 41 : Parse the output from FingerPrintScan for proteins 1 to 3 has failed irretrievably.  Available StackTraces follow.
2015-08-19 14:30:48,652 [uk.ac.ebi.interpro.scan.jms.activemq.NonZeroExitOnUnrecoverableError:41] FATAL - The JVM will now exit with a non-zero exit status.
2015-08-19 14:30:48,652 [uk.ac.ebi.interpro.scan.jms.master.StandaloneBlackBoxMaster:107] ERROR - Exception thrown by StandaloneBlackBoxMaster: 
java.lang.IllegalStateException: InterProScan exiting with non-zero status, see logs for further information.
	at uk.ac.ebi.interpro.scan.jms.activemq.NonZeroExitOnUnrecoverableError.failed(NonZeroExitOnUnrecoverableError.java:42)
	at uk.ac.ebi.interpro.scan.jms.master.StandaloneBlackBoxMaster.run(StandaloneBlackBoxMaster.java:49)
	at uk.ac.ebi.interpro.scan.jms.main.Run.main(Run.java:290)
InterProScan analysis failed. Exception thrown by StandaloneBlackBoxMaster. Check the log file for details
CAN U HELP :confused: :(

---

