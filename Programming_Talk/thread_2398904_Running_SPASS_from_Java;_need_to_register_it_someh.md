---
title: "Running SPASS from Java; need to register it somehow?"
date: 2018-08-19
forum: Programming Talk
---

### Post by fravec on 2018-08-19
Hey community!

I would like to run the program SPASS (see [https://www.mpi-inf.mpg.de/departments/automation-of-logic/software/spass-workbench/classic-spass-theorem-prover/download/](https://www.mpi-inf.mpg.de/departments/automation-of-logic/software/spass-workbench/classic-spass-theorem-prover/download/)) from Java. The following code should run it and print its output; well it at least does so, when replacing the literal "SPASS" by "gedit" for instance:
```

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class EntryPoint {

    public static void main(String[] args) throws IOException, InterruptedException {
        String cmd = "SPASS";
        Runtime run = Runtime.getRuntime();
        Process pr = run.exec(cmd);
        pr.waitFor();
        BufferedReader buf = new BufferedReader(new InputStreamReader(pr.getInputStream()));
        String line = "";
        while ((line = buf.readLine()) != null) {
            System.out.println(line);
        }
    }
}
```
In case you are familiar with jshell, you can minimise the example to the following:
```

$ jshell 
|  Welcome to JShell -- Version 10.0.1
|  For an introduction type: /help intro

jshell> var run = Runtime.getRuntime();
run ==> java.lang.Runtime@6f7fd0e6

jshell> run.exec("SPASS");
|  java.io.IOException thrown: Cannot run program "SPASS": error=2, No such file or directory
|        at ProcessBuilder.start (ProcessBuilder.java:1128)
|        at ProcessBuilder.start (ProcessBuilder.java:1071)
|        at Runtime.exec (Runtime.java:635)
|        at Runtime.exec (Runtime.java:459)
|        at Runtime.exec (Runtime.java:356)
|        at (#2:1)

```

In ~/.bashrc I registered the program via an alias:
```
alias SPASS='~/Desktop/SPASS-3.5/SPASS'
```
which does work, when run on the terminal
```
$ SPASS

              /home/jfd/Desktop/SPASS-3.5/SPASS V 3.5
           Usage: SPASS [options] [<input-file>] 

Possible options:

Auto               Stdin              Interactive        Flotter            
SOS                Splits             SplitMinInst       Memory             
TimeLimit          DocSST             DocProof           DocSplit           
Loops              PSub               PRew               PCon               
PTaut              PObv               PSSi               PSST               
PMRR               PUnC               PAED               PDer               
PGiven             PLabels            PKept              PProblem           
PEmptyClause       PStatistic         FPModel            FPDFGProof         
PFlags             POptSkolem         PStrSkolem         PBDC               
PBInc              PApplyDefs         Select             RInput             
Sorts              SatInput           WDRatio            PrefCon            
FullRed            FuncWeight         VarWeight          PrefVar            
BoundMode          BoundStart         BoundLoops         ApplyDefs          
Ordering           CNFQuantExch       CNFOptSkolem       CNFStrSkolem       
CNFProofSteps      CNFSub             CNFCon             CNFRedTimeLimit    
CNFRenaming        CNFRenMatch        CNFPRenaming       CNFFEqR            
IEmS               ISoR               IEqR               IERR               
IEqF               IMPm               ISpR               IOPm               
ISPm               ISpL               IORe               ISRe               
ISHy               IOHy               IURR               IOFc               
ISFc               IUnR               IBUR               IDEF               
RFRew              RBRew              RFMRR              RBMRR              
RObv               RUnC               RTer               RTaut              
RSST               RSSi               RFSub              RBSub              
RAED               RCon               TDfg2OtterOptions  EML                
EMLAuto            EMLTranslation     EML2Rel            EMLTheory          
EMLFuncNdeQ        EMLFuncNary        EMLFFSorts         EMLElimComp        
EMLPTrans          TPTP               rf 

```

Do I have to register the program in Ubuntu as an actual program in the application management? I would like to run my program on any OS with a prerequirement of a runnable "SPASS" macro pointing to the program, so giving a path is a bad option, but it remains an alternative if nothing else works.

Thank you in advance!

---

### Post by spjackson on 2018-08-19
The alias command only has significance to bash. Neither java nor exec are aware of it. If you don't want to specify the path to SPASS in your program, then you need to put it on your PATH. e.g.
```

export PATH=$PATH:~/Desktop/SPASS-3.5
jshell

```

---

### Post by fravec on 2018-08-20
It looks like it only works with jshell and not with a compiled Java program. Also, I was looking for something that manipulates my PATH-variable in such manner, that I can execute the program living in ~/Desktop/SPASS-3.5 by running "SPASS" instead of running "~/Desktop/SPASS-3.5/SPASS".

---

