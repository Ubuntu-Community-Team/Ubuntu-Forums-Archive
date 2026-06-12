---
title: "SPOJ problem"
date: 2009-03-12
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-03-12
I am not telling anyone here to help me solve the problem.

My code is working for the sum given, but i am facing difficulty taking input for the sum. No one on the spoj forums was helping. Can someone over here please help me.
The sum is at 
[http://www.spoj.pl/problems/BASE/](http://www.spoj.pl/problems/BASE/)

```

def main():
        d={'0':0,'1':1,'2':2,'3':3,'4':4,'5':5,'6':6,'7':7,'8':8,'9':9,'A':10,'B':11,'C':12,'D':13,'E':14,'F':15}
        e={0:'0',1:'1',2:'2',3:'3',4:'4',5:'5',6:'6',7:'7',8:'8',9:'9',10:'A',11:'B',12:'C',13:'D',14:'E',15:'F'}
i=0        
        while i!=1:
                try:
                        i=raw_input("")
                        i=i.lstrip(' ')
                        if i.find('  ')!=-1:
                                g=i.find('  ')
                                i=list(i)
                                del i[g]
                                i=''.join(i)
                        if i.find('  ')!=-1:
                                g=i.find('  ')
                                i=list(i)
                                del i[g]
                                i=''.join(i)
                        a,b,c=i.split(' ')
                        b,k,c=int(b),len(a),int(c)
                        ans=[]
                        a=list(a)
                        a.reverse()
                        a=''.join(a)
                        dec=0
                        for j in range(k):
                                dec=dec+(d[a[j]]*(b**j))
                        for j in range(7):
                                rem=dec%c
                                dec=dec/c
                                ans.append(e[rem])
                        ans.reverse()
                        ans=''.join(ans)
                        ans=ans.lstrip('0')
                        if dec!=0:
                                ans="ERROR"
                        print "%7s"%ans
                except EOFError:
                        break
                except ValueError:
                        continue
main()

```

I am fairly noob in programming so excuse my length procedure. But the thing is it works. But i dont know how to take input for the sum. Can someone help.

---

### Post by ridowan007 on 2010-02-07
try to use i=raw_input().split()

then i[0] is your first,i[1] 2nd & i[2] 3rd input.

---

