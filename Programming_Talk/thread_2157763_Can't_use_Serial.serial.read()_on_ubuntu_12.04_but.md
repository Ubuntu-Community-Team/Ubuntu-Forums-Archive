---
title: "Can't use Serial.serial.read() on ubuntu 12.04 but it is working fine on ubuntu 10.04"
date: 2013-06-26
forum: Programming Talk
---

### Post by wlsgus728 on 2013-06-26
I was using ubuntu 10.04 and now updating to ubuntu 12.04 but one of my python code was working fine in ubuntu 10.04 but not in ubuntu 12.04.(Ubuntu 10.04: python version = 2.6.5, Ubuntu 12.04: python version = 2.7.3)
Here is my code.

---

### Post by wlsgus728 on 2013-06-26
I was wondering if this is not working due to the difference of  baudrate. I checked baudrate with minicom and set it 19200 for every  case. I don't know if it helped [IMG]https://forums.opensuse.org/images/smiliesnew/sad.png[/IMG]

---

### Post by Vaphell on 2013-06-26
python without indentation? o.O
wrap the indented code in [code][/****code] tags or nobody will look at this

---

### Post by wlsgus728 on 2013-06-27
sorry I didn't know how to put that. I just fixed it

---

### Post by wlsgus728 on 2013-06-27
um... somehow I was editing and could not edit any more. here is what I wrote before. "I was using ubuntu 10.04 and now updating to ubuntu 12.04 but one of my python code was working fine in ubuntu 10.04 but not in ubuntu 12.04.(Ubuntu 10.04: python version = 2.6.5, Ubuntu 12.04: python version = 2.7.3)
Here is my code.
"```
class FTSensor:
    def __init__(self, dev, baudrate=19200):
        print 'FTSensor: opening serial port (baudrate =', baudrate, ')'
        self.ftcon = serial.Serial(dev,timeout  =0.1)
        print 'FTSensor: setting properties'
        self.ftcon.setBaudrate(baudrate)
        self.ftcon.setParity('N')
        self.ftcon.setStopbits(1)
        self.ftcon.open()

        #self.RESET_INTERVAL=1.0 #seconds until transmittion is reset to fix bug
        count = 0
        self.reset_time = None
        self.reset()
        while not self._start_query():
            rospy.logwarn('FTSensor: resetting')
            count = count + 1
            self.reset()
            if count == 10:
                rospy.logfatal('FTSensor.__init__: Too many resets.  Try manually restarting FT sensors.')

        #self.last_access = time.time()
        self.last_value = []

    def read(self):
        #rospy.logwarn('READ')

        current_value = self.last_value

        #rospy.logwarn(current_value)

        #rospy.logwarn('READ-BEFORE while')
        while current_value == self.last_value:
            #rospy.logwarn('READ-INSIDE while')
            **t = self.ftcon.read(19)**
            leng = t[0]
            print leng
            rospy.logwarn(t) 
            #if we get an error message, restart
            if len(t) < 1 or ord(t[0]) != 0 or len(t) < 10:
            rospy.logwarn('READ-WHILE-if')                
            #pass
                #self.reset()
                print 'exiting due to if len(t) < 1 or ord(t[0]) != 0 or len(t) < 10'
                print 't is', t
                exit()
                while not self._start_query():
                    #self.reset()
                    print 'exiting due to not self._start_query()'
                    print 't is', t
                    exit()
                break
            else:
            #rospy.logwarn('READ-WHILE-else') 
                current_value = t
                #current_value = binary_to_ft(t)

        self.last_value = current_value
        return current_value
``` .... ... I did not put the main function but the one I highlighted(**t = self.ftcon.read(19)**) was the problem. From ubuntu 10.04 it was fine but from ubuntu 12.04, it gives strange values like "D R .cracked letter" The type of t is list so it wouldnt give me a number but I have no idea where D and R came from.
Is there something in particular I need to check?
Thanks.

---

