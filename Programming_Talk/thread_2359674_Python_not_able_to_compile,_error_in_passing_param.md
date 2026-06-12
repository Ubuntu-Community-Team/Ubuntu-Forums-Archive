---
title: "Python: not able to compile, error in passing parameter to constructor"
date: 2017-04-26
forum: Programming Talk
---

### Post by houmingc on 2017-04-26
I create 'myscope' an object class named scope & passing it parameter('TCPIP::169.254.118.184 ::INSTR') 
I could not assign visa_address to num.
If i write the python constructor outside the class, the program work.

!/usr/bin/python
import os
import visa


class Scope(object):
    """ Measure Wave from oscilloscope
    """    
    def __init__(self,num):
        self.n=num
        print self.n
        try:
            visa_address=self.n
            rm= visa.ResourceManager('@py')
            scope = rm.get_instrument(visa_address)
            scope.timeout =1000
        except IOError:
            print 'Cannot connect!!' 
            scope.write('SING;*OPC?')
    def drive(self): print("Equipment Oscilloscope.")
    def FreqMeas(self):
        scope.write('MEAS1:SOUR C1W1')  #configure channel1 as source
        scope.write('MEAS1:MAIN FREQ')  #configure frequency as input
        scope.write('MEAS1 ON')         #measure start to capture
        scope.write('*OPC?')            #operation complete
        self.valueRet=scope.ask('MEAS1:RES:ACT?')   #get measurement 
        return self.valueRet
    def AmpMeas(self):
        scope.write('MEAS1:SOUR C1W1')  #configure channel1 as source
        scope.write('MEAS1:MAIN AMPL')  #configure amplitude as input
        scope.write('MEAS1 ON')         #configure  tart to capture
        scope.write('*OPC?')            #operation complete
        self.valueRet=scope.ask('MEAS1:RES:ACT?')   #get measurement 
        return self.valueRet
    def PeriodMes(self):
        scope.write('MEAS1:SOUR C1W1')  #configure channel1 as source
        scope.write('MEAS1:MAIN PER')  #configure period as input
        scope.write('MEAS1 ON')         #configure start to capture
        scope.write('*OPC?')            #operation complete
        self.valueRet=scope.ask('MEAS1:RES:ACT?')   #get measurement
        return self.valueRet
    def BwMeas(self):
        scope.write('MEAS1:SOUR C1W1')  #configure channel1 as source
        scope.write('MEAS1:MAIN BWID')  #configure bandwidth as input
        scope.write('MEAS1 ON')         #configure start to capture
        scope.write('*OPC?')            #operation complete
        self.valueRet=scope.ask('MEAS1:RES:ACT?')   #get measurement 
        return self.valueRet
    def DcMeas(self):
        scope.write('MEAS1:SOUR C1W1')  #configure channel1 as source
        scope.write('MEAS1:MAIN PDCY')  #configure dutyCycle as input
        scope.write('MEAS1 ON')         #configure start to capture
        scope.write('*OPC?')            #operation complete
        self.valueRet=scope.ask('MEAS1:RES:ACT?')   #get measurement
        print 'valueRet= ',valueRet
        tt_list.append(valueRet)
        return self.valueRet
    def PtMeas(self):
        scope.write('MEAS1:SOUR C1W1')  #configure channel1 as source
        scope.write('MEAS1:MAIN PULS')  #configure pulsetrain as input
        scope.write('MEAS1 ON')         #configure start to capture
        scope.write('*OPC?')            #operation complete
        self.valueRet=scope.ask('MEAS1:RES:ACT?')   #get measurement
        tt_list.append(valueRet)
        return self.valueRet
    def RisetimeMeas(self):
        scope.write('MEAS1:SOUR C1W1')  #configure channel1 as source
        scope.write('MEAS1:MAIN RTIM')  #configure RISETIME as input
        scope.write('MEAS1 ON')         #configure start to capture
        scope.write('*OPC?')            #operation complete
        self.valueRet=scope.ask('MEAS1:RES:ACT?')   #get measurement 
        tt_list.append(valueRet)
        return self.valueRet
    def FalltimeMeas(self):
        scope.write('MEAS1:SOUR C1W1')  #configure channel1 as source
        scope.write('MEAS1:MAIN FTIM')  #configure FallTime as input
        scope.write('MEAS1 ON')         #configure start to capture
        scope.write('*OPC?')            #operation complete
        self.valueRet=scope.ask('MEAS1:RES:ACT?')   #get measurement 
        return self.valueRet





tt_list= []
valueRet=0

myscope = Scope('TCPIP::169.254.118.184 ::INSTR')         # creating myscope object class scope
freq1=myscope.FreqMeas()
print 'Frequency is',freq1

fallTime = myscope.FalltimeMeas()
print 'fallTime is',fallTime

riseTime = myscope.RisetimeMeas()
print 'riseTime is',riseTime

---

