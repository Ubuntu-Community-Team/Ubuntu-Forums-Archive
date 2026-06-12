---
title: "terrible map() function performance in python"
date: 2009-03-13
forum: Programming Talk
---

### Post by blake82 on 2009-03-13
Hi,

I'm having an odd experience with the map() function in python 2.5.

I'm processing some lists of numbers (less than 3000 x 10 x 2 elements or 3000 x 4 elements depending on the function), and I'm passing it through really simple functions like:

```
def addn(inputs):
    ans = [0, 0]
    ans[0] = (inputs[0] + inputs[1])
    ans[1] = (inputs[2] + inputs[3])
    return ans
```

or

```
def ravg(inputs):
    ans = [0, 0]
    ans[0] = (sum(inputs[0]) / len(inputs[0]))
    ans[1] = (sum(inputs[1]) / len(inputs[1]))
    return ans
```

and it's taking FOREVER. The ravg function listed above takes can take upwards of 2-3 minutes to finish computing 3000 x 2 sets of data, with 10 elements to average out. The addn takes 3 seconds sometimes.

Any idea what might be causing this? My understanding is that the map function was supposed to be fastest for repetitive tasks like this.

Also, memory is not an issue, I've got about 900MB free and nothing's going into swap.

Let me know what you think

Thanks,

Blake

---

### Post by ghostdog74 on 2009-03-13
show the whole code

---

### Post by blake82 on 2009-03-13
Here you go:

```
            for g in self.lstNrml:
                #get node number
                self.n = g
                #get addreses
                self.ad1 = self.addr01[self.n]
                self.an1 = outNum(self.ad1)
                self.ad2 = self.addr02[self.n]
                self.an2 = outNum(self.ad2)
                self.ad3 = self.addr03[self.n]
                self.an3 = outNum(self.ad3)
                self.ad4 = self.addr04[self.n]
                self.an4 = outNum(self.ad4)
                #get node op
                self.op = self.nodeOp[self.n]
                
                #check if this is a list node
                if(self.op in prm.dataPrm):
                    #get list index
                    self.idxList = self.lstList.index(self.n)
                    #update instance lists
                    map(self.updateList, self.lstActv)
                    
                    #get input values
                    tList = map(self.getList, self.lstActv)
                    
                    #route list based on nodeOp
                    t1 = time.time()
                    if(self.op == "ravg"):
                        self.lstValu = map(prm.ravg, tList)
                    elif(self.op == "rsdv"):
                        self.lstValu = map(prm.rsdv, tList)
                    elif(self.op == "corr"):
                        self.lstValu = map(prm.corr, tList)
                    elif(self.op == "vmin"):
                        self.lstValu = map(prm.vmin, tList)
                    elif(self.op == "vmax"):
                        self.lstValu = map(prm.vmax, tList)
                    t2 = time.time()
                    print (t2-t1), "seconds"
                    #pass solutions back to instances
                    map(self.updateOutput, self.lstActv, self.lstValu)
                #otherwise, process normally
                else:
                    #get input values
                    tList = map(self.getVal, self.lstActv)
                    t1 = time.time()
                    if(self.op == "addn"):
                        self.lstValu = map(prm.addn, tList)
                    elif(self.op == "subt"):
                        self.lstValu = map(prm.subt, tList)
                    elif(self.op == "divn"):
                        self.lstValu = map(prm.divn, tList)
                    elif(self.op == "mult"):
                        self.lstValu = map(prm.mult, tList)
                    elif(self.op == "sqrt"):
                        self.lstValu = map(prm.sqrt, tList)
                    elif(self.op == "absv"):
                        self.lstValu = map(prm.absv, tList)
                    elif(self.op == "logr"):
                        self.lstValu = map(prm.logr, tList)
                    elif(self.op == "degr"):
                        self.lstValu = map(prm.degr, tList)
                    elif(self.op == "radi"):
                        self.lstValu = map(prm.radi, tList)
                    elif(self.op == "imin"):
                        self.lstValu = map(prm.imin, tList)
                    elif(self.op == "imax"):
                        self.lstValu = map(prm.imax, tList)
                    elif(self.op == "iavg"):
                        self.lstValu = map(prm.iavg, tList)
                    elif(self.op == "isdv"):
                        self.lstValu = map(prm.isdv, tList)
                    t2 = time.time()
                    print (t2-t1), "seconds"

                    #pass solutions back to instances
                    map(self.updateOutput, self.lstActv, self.lstValu)
```

and then it calls these functions:

```
def addn(inputs):
    ans = [0, 0]
    ans[0] = (inputs[0] + inputs[1])
    ans[1] = (inputs[2] + inputs[3])
    return ans

def subt(inputs):
    ans = [0, 0]
    ans[0] = (inputs[0] - inputs[1])
    ans[1] = (inputs[2] - inputs[3])
    return ans

def divn(inputs):
    ans = [0, 0]
    ans[0] = (inputs[0] / inputs[1])
    ans[1] = (inputs[2] / inputs[3])
    return ans
    
def mult(inputs):
    ans = [0, 0]
    ans[0] = (inputs[0] * inputs[1])
    ans[1] = (inputs[2] * inputs[3])
    return ans

def sqrt(inputs):
    ans = [0, 0]
    ans[0] = math.sqrt(abs(inputs[0]))
    ans[1] = math.sqrt(abs(inputs[1]))
    return ans

def absv(inputs):
    ans = [0, 0]
    ans[0] = (abs(inputs[0]))
    ans[1] = (abs(inputs[1]))
    return ans

def logr(inputs):
    ans = [0, 0]
    ans[0] = math.log(abs(inputs[0]))
    ans[1] = math.log(abs(inputs[1]))
    return ans
    
def degr(inputs):
    ans = [0, 0]
    ans[0] = math.degrees(inputs[0])
    ans[1] = math.degrees(inputs[1])
    return ans

def radi(inputs):
    ans = [0, 0]
    ans[0] = math.radians(inputs[0])
    ans[1] = math.radians(inputs[1])
    return ans

def imin(inputs):
    ans = [0, 0]
    x = min(inputs)
    ans[0] = x
    ans[1] = x
    return ans

def imax(inputs):
    ans = [0, 0]
    x = max(inputs)
    ans[0] = x
    ans[1] = x
    return ans

def iavg(inputs):
    ans = [0, 0]
    x = (sum(inputs)/4)
    ans[0] = x
    ans[1] = x
    return ans

def isdv(inputs):
    ans = [0, 0]
    x = (sum(inputs)/4)
    devs = [0, 0, 0, 0]

    for i in range(0, 4):
        devs[i] = square(inputs[i] - x)
        
    a = math.sqrt(sum(devs) / 3) / x
    ans[0] = a
    ans[1] = a
    return ans

def vmin(inputs):
    ans = [0, 0]
    ans[0] = min(inputs[0])
    ans[1] = min(inputs[1])
    return ans

def vmax(inputs):
    ans = [0, 0]
    ans[0] = max(inputs[0])
    ans[1] = max(inputs[1])
    return ans

def ravg(inputs):
    ans = [0, 0]
    ans[0] = (sum(inputs[0]) / len(inputs[0]))
    ans[1] = (sum(inputs[1]) / len(inputs[1]))
    return ans
    
def rsdv(inputs):
    #compute mean
    avg = [0, 0]
    avg[0] = (sum(inputs[0]) / len(inputs[0]))
    avg[1] = (sum(inputs[1]) / len(inputs[1]))
    
    #add up val - avg
    devs = [[], []]
    i = 0
    for i in range(0, len(inputs[0])):
        devs[0].append(square(inputs[0][i] - avg[0]))
        devs[1].append(square(inputs[1][i] - avg[1]))
    
    ans = [0, 0]
    if(len(inputs[0]) > 1):
        if(avg[0] == 0):
            ans[0] = 0
        else:
            ans[0] = math.sqrt(sum(devs[0]) / (len(devs[0]) - 1))/avg[0]
        if(avg[1] == 0):
            ans[1] = 0
        else:
            ans[1] = math.sqrt(sum(devs[1]) / (len(devs[1]) - 1))/avg[1]
    else:
        ans = [0, 0]
    
    return ans

def corr(inputs):
    ans = [0, 0]
    
    if(len(inputs[0]) > 1):
        #declare classes
        corrW = genCompute.fitScore()
        corrX = genCompute.fitScore()
        corrY = genCompute.fitScore()
        corrZ = genCompute.fitScore()
        
        #enter values in statistics classes
        numEle = len(inputs[0])
        i = 0
        for i in range(0, numEle):
            corrW.entryTally(inputs[0][i])
            corrW.enter(inputs[0][i])
            
            corrX.entryTally(inputs[1][i])
            corrX.enter(inputs[1][i])
            
            corrY.entryTally(inputs[2][i])
            corrY.enter(inputs[2][i])
            
            corrZ.entryTally(inputs[3][i])
            corrZ.enter(inputs[3][i])
        
        #get stats
        wMean = corrW.getMean()
        wStDev = corrW.getStDev()
        
        xMean = corrX.getMean()
        xStDev = corrX.getStDev()
        
        yMean = corrY.getMean()
        yStDev = corrY.getStDev()
        
        zMean = corrZ.getMean()
        zStDev = corrZ.getStDev()
        
        aSum = 0
        bSum = 0
        for i in range(0, numEle):
            
            aSum = aSum + ((inputs[0][i] - wMean) * (inputs[1][i] - xMean))
            bSum = bSum + ((inputs[2][i] - yMean) * (inputs[3][i] - zMean))
        
        wxdNom = (wStDev * xStDev * (numEle - 1))
        yzdNom = (yStDev * zStDev * (numEle - 1))
        
        if(wxdNom == 0):
            ans[0] = 0
        else:
            ans[0] = aSum / wxdNom
        
        if(yzdNom == 0):
            ans[1] = 0
        else:
            ans[1] = bSum / yzdNom
    
    return ans
```

---

### Post by smartbei on 2009-03-13
The first thing I notice that could probably cut the time significantly is that your functions all have the odd convention of creating the list to be returned, and then editing its values and returning it. For example, in the function addn, you create the list ans, edit its values, and then return it. Why not just return the values? For example, the function addn would be:
```

def addn(inputs):
    return [inputs[0] + inputs[1], inputs[2] + inputs[3]]

```
On my computer this takes 0.7 times as much time as the original function.

---

### Post by blake82 on 2009-03-13
Yeah, this is my first python program, so there are some odd things like that here and there I need to go through and fix.

Do you think the constant allocation and unallocation of memory might be one of the reasons behind the delay?

---

