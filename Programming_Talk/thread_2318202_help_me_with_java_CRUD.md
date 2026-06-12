---
title: "help me with java CRUD"
date: 2016-03-23
forum: Programming Talk
---

### Post by thegamer2 on 2016-03-23
i want to add a new column to my database with java , i use eclipse 

i put the the UI in a class and the activity in other class
this is the code

```
public class Emp {
    private Connection con;
    private int EMPNO;
    private String ENAME;
    private String JOB;
    private int SAL;
    private String EMAIL_EMP;
    public int getEMPno() {
        return EMPNO;
    }
    public void setEMPno(int eMPno) {
        EMPNO = eMPno;
    }
    public String getENAME() {
        return ENAME;
    }
    public void setENAME(String eNAME) {
        ENAME = eNAME;
    }
    public String getJOB() {
        return JOB;
    }
    public void setJOB(String jOB) {
        JOB = jOB;
    }
    public int getSAL() {
        return SAL;
    }
    public void setSAL(int sAL) {
        SAL = sAL;
    }
    public String getEMAIL_EMP() {
        return EMAIL_EMP;
    }
    public void setEMAIL_EMP(String eMAIL_EMP) {
        EMAIL_EMP = eMAIL_EMP;
    }
    public Emp(int eMPno, String eNAME, String jOB, int sAL, String eMAIL_EMP) {
        super();
        EMPNO = eMPno;
        ENAME = eNAME;
        JOB = jOB;
        SAL = sAL;
        EMAIL_EMP = eMAIL_EMP;
    }
    public Emp() {
        super();
    }
    
    
    public void addemp(int EMPNO, String ENAME, String JOB, int SAL,String EMAIL_EMP) throws SQLException {
        String requette = "INSERT INTO `emp` (`EMPNO` ,`ENAME` ,`JOB` ,`SAL`,`EMAIL_EMP`)" +
                "VALUES (?, ?, ?, ?,?)";
        PreparedStatement ps = con.prepareStatement(requette);
        ps.setInt(1, EMPNO);
        ps.setString(2, ENAME);
        ps.setString(3, JOB);
        ps.setInt(4, SAL);
        ps.setString(5, EMAIL_EMP);
        ps.executeUpdate();
    }


```

and the other class



```
JButton btnAdd = new JButton("add");
        btnAdd.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent arg0) {
                
            
            try {
                Connect c=new Connect();
                c.connexionBD();
                Emp a=new Emp();
                a.addemp(Integer.parseInt(txtno.getText()), txtname.getText(), txtjob.getText(),Integer.parseInt(txtsal.getText()), txtemail.getText());
            } catch (SQLException e) {
                // 
                
            }
            
            }
        }

```


help me please and thanks

---

### Post by QIII on 2016-03-23
You are trying to add a row (or tuple), not a column.

Are you asking the community to review your code?  Is the problem that it won't compile?  Does it throw exception when you run it?

Is this for school?

---

### Post by thegamer2 on 2016-03-24
i got this 
```

driver etablie
connexion base orcl etablie
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at Connection.Emp.addemp(Emp.java:60)
	at Connection.ADDemp$2.actionPerformed(ADDemp.java:106)
	at javax.swing.AbstractButton.fireActionPerformed(Unknown Source)
	at javax.swing.AbstractButton$Handler.actionPerformed(Unknown Source)
	at javax.swing.DefaultButtonModel.fireActionPerformed(Unknown Source)
	at javax.swing.DefaultButtonModel.setPressed(Unknown Source)
	at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(Unknown Source)
	at java.awt.Component.processMouseEvent(Unknown Source)
	at javax.swing.JComponent.processMouseEvent(Unknown Source)
	at java.awt.Component.processEvent(Unknown Source)
	at java.awt.Container.processEvent(Unknown Source)
	at java.awt.Component.dispatchEventImpl(Unknown Source)
	at java.awt.Container.dispatchEventImpl(Unknown Source)
	at java.awt.Component.dispatchEvent(Unknown Source)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Unknown Source)
	at java.awt.LightweightDispatcher.processMouseEvent(Unknown Source)
	at java.awt.LightweightDispatcher.dispatchEvent(Unknown Source)
	at java.awt.Container.dispatchEventImpl(Unknown Source)
	at java.awt.Window.dispatchEventImpl(Unknown Source)
	at java.awt.Component.dispatchEvent(Unknown Source)
	at java.awt.EventQueue.dispatchEventImpl(Unknown Source)
	at java.awt.EventQueue.access$300(Unknown Source)
	at java.awt.EventQueue$3.run(Unknown Source)
	at java.awt.EventQueue$3.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.security.ProtectionDomain$1.doIntersectionPrivilege(Unknown Source)
	at java.security.ProtectionDomain$1.doIntersectionPrivilege(Unknown Source)
	at java.awt.EventQueue$4.run(Unknown Source)
	at java.awt.EventQueue$4.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.security.ProtectionDomain$1.doIntersectionPrivilege(Unknown Source)
	at java.awt.EventQueue.dispatchEvent(Unknown Source)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
	at java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
	at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
	at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
	at java.awt.EventDispatchThread.run(Unknown Source)
```
and yes it's for school :)

---

### Post by howefield on 2016-03-24
Thread closed.

> 
While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.

---

