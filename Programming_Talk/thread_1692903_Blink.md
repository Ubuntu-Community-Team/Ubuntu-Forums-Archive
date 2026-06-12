---
title: "Blink"
date: 2011-02-22
forum: Programming Talk
---

### Post by tzeronone on 2011-02-22
I am new in this NesC programming. But I have already have the code for "Blink" application which is very basic. But when I compiled the code, there are a lot of error.
Can anyone help me to correct the code?
Thank you.

#MAKEFILE
COMPONENT=Blink
include $(Makerules)

#BLINK.NC
configuration Blink {
}
implementation {
  components Main, BlinkM, SingleTimer, LedsC;
  Main.StdControl -> SingleTimer.StdControl;
  Main.StdControl -> BlinkM.StdControl;
  BlinkM.Timer -> SingleTimer.Timer;
  BlinkM.Leds -> LedsC;
}

#BLINKM.NC
module BlinkM {
  provides {
    interface StdControl;
  }
  uses {
    interface Timer;
    interface Leds;
  }
}
implementation {

  command result_t StdControl.init() {
    call Leds.init(); 
    return SUCCESS;
  }


  command result_t StdControl.start() {
    // Start a repeating timer that fires every 1000ms
    return call Timer.start(TIMER_REPEAT, 1000);
  }

  command result_t StdControl.stop() {
    return call Timer.stop();
  }


  event result_t Timer.fired()
  {
    call Leds.redToggle();
    return SUCCESS;
  }
}

#SINGLE TIMER.NC
configuration SingleTimer {
  
provides interface Timer;
  provides interface StdControl;
}

implementation {
  components TimerC;
  
  Timer = TimerC.Timer[unique("Timer")];
  StdControl = TimerC;
}

But I had this error:
In component 'Blink':
Blink.nc:5 component Main not found
In file included from Blink.nc:5:
In component 'BlinkM':
BlinkM.nc:7: too few arguments to interface 'Tiner'
In file included from Blink.nc:5:
BlinkM.nc:13: syntax error before 'StdControl'
BlinkM: 'StdControl.start' not implemented
BlinkM: 'StdControl.stop' not implemented
BlinkM: 'Timer.fired' not implemented
In file included from Blink.nc.5:
In component 'SingleTimer':
SIngleTimer.nc:2: too few arguments to interface 'Timer'
SingleTimer.nc;7: component TimerC not found
SingleTimer.nc:8: cannot find 'Timer'
SingleTimer.nc:9: no match
In component 'Blink':
Blink.nc:6: cannot find 'StdControl'
Blink.nc:7: cannot find 'StdCOntrol'
make: *** [exe0] Error 1

---

### Post by tzeronone on 2011-02-22
**Blink** 			
 			 			 		   		 		 		I am new in this NesC programming. But I have already have the code for "Blink" application which is very basic. But when I compiled the code, there are a lot of error.
Can anyone help me to correct the code?
Thank you.

#MAKEFILE
COMPONENT=Blink
include $(Makerules)

#BLINK.NC
configuration Blink {
}
implementation {
  components Main, BlinkM, SingleTimer, LedsC;
  Main.StdControl -> SingleTimer.StdControl;
  Main.StdControl -> BlinkM.StdControl;
  BlinkM.Timer -> SingleTimer.Timer;
  BlinkM.Leds -> LedsC;
}

#BLINKM.NC
module BlinkM {
  provides {
    interface StdControl;
  }
  uses {
    interface Timer;
    interface Leds;
  }
}
implementation {

  command result_t StdControl.init() {
    call Leds.init(); 
    return SUCCESS;
  }


  command result_t StdControl.start() {
    // Start a repeating timer that fires every 1000ms
    return call Timer.start(TIMER_REPEAT, 1000);
  }

  command result_t StdControl.stop() {
    return call Timer.stop();
  }


  event result_t Timer.fired()
  {
    call Leds.redToggle();
    return SUCCESS;
  }
}

#SINGLE TIMER.NC
configuration SingleTimer {
  
provides interface Timer;
  provides interface StdControl;
}

implementation {
  components TimerC;
  
  Timer = TimerC.Timer[unique("Timer")];
  StdControl = TimerC;
}

But I had this error:
In component 'Blink':
Blink.nc:5 component Main not found
In file included from Blink.nc:5:
In component 'BlinkM':
BlinkM.nc:7: too few arguments to interface 'Tiner'
In file included from Blink.nc:5:
BlinkM.nc:13: syntax error before 'StdControl'
BlinkM: 'StdControl.start' not implemented
BlinkM: 'StdControl.stop' not implemented
BlinkM: 'Timer.fired' not implemented
In file included from Blink.nc.5:
In component 'SingleTimer':
SIngleTimer.nc:2: too few arguments to interface 'Timer'
SingleTimer.nc;7: component TimerC not found
SingleTimer.nc:8: cannot find 'Timer'
SingleTimer.nc:9: no match
In component 'Blink':
Blink.nc:6: cannot find 'StdControl'
Blink.nc:7: cannot find 'StdCOntrol'
make: *** [exe0] Error 1

---

### Post by tzeronone on 2011-02-22
**Blink**             
                                                                I am new in this NesC programming. But I have already have the code for "Blink" application which is very basic. But when I compiled the code, there are a lot of error.
Can anyone help me to correct the code?
Thank you.

#MAKEFILE
COMPONENT=Blink
include $(Makerules)

#BLINK.NC
configuration Blink {
}
implementation {
  components Main, BlinkM, SingleTimer, LedsC;
  Main.StdControl -> SingleTimer.StdControl;
  Main.StdControl -> BlinkM.StdControl;
  BlinkM.Timer -> SingleTimer.Timer;
  BlinkM.Leds -> LedsC;
}

#BLINKM.NC
module BlinkM {
  provides {
    interface StdControl;
  }
  uses {
    interface Timer;
    interface Leds;
  }
}
implementation {

  command result_t StdControl.init() {
    call Leds.init(); 
    return SUCCESS;
  }


  command result_t StdControl.start() {
    // Start a repeating timer that fires every 1000ms
    return call Timer.start(TIMER_REPEAT, 1000);
  }

  command result_t StdControl.stop() {
    return call Timer.stop();
  }


  event result_t Timer.fired()
  {
    call Leds.redToggle();
    return SUCCESS;
  }
}

#SINGLE TIMER.NC
configuration SingleTimer {
  
provides interface Timer;
  provides interface StdControl;
}

implementation {
  components TimerC;
  
  Timer = TimerC.Timer[unique("Timer")];
  StdControl = TimerC;
}

But I had this error:
In component 'Blink':
Blink.nc:5 component Main not found
In file included from Blink.nc:5:
In component 'BlinkM':
BlinkM.nc:7: too few arguments to interface 'Tiner'
In file included from Blink.nc:5:
BlinkM.nc:13: syntax error before 'StdControl'
BlinkM: 'StdControl.start' not implemented
BlinkM: 'StdControl.stop' not implemented
BlinkM: 'Timer.fired' not implemented
In file included from Blink.nc.5:
In component 'SingleTimer':
SIngleTimer.nc:2: too few arguments to interface 'Timer'
SingleTimer.nc;7: component TimerC not found
SingleTimer.nc:8: cannot find 'Timer'
SingleTimer.nc:9: no match
In component 'Blink':
Blink.nc:6: cannot find 'StdControl'
Blink.nc:7: cannot find 'StdCOntrol'
make: *** [exe0] Error 1

---

### Post by cavh on 2011-02-22
Suggest you move this question to the programming forum at [http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by The Cog on 2011-02-22
Moved to Programming Talk. It won't get buried so quickly there. I can't help you with your problem though - I don't even recognise the language you're using.

---

### Post by howefield on 2011-02-22
Moved to "*Programming Talk*" to increase your chances of getting help.

---

### Post by cariboo on 2011-02-22
I merged three threads on the same subject. Please don't create multiple threads on the same subject.

---

### Post by Zugzwang on 2011-02-22
@OP: Most of the people will not be familiar with the programming language you used here. Perhaps you start by giving some details on it.

Then, check how it can be that the word "Tiner" occurs in the first error message you pasted, but the respective code line contains only "Timer". Is is possible that the code that you are trying to compile is not the same the one that you pasted?

---

