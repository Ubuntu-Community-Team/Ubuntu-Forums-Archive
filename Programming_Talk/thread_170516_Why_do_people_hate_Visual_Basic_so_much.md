---
title: "Why do people hate Visual Basic so much?"
date: 2006-05-04
forum: Programming Talk
---

### Post by drpolish on 2006-05-04
It's such an easy language to use, but it isn't cross-platform. But what are your other gripes on VB? VB.NET? Because of all these complaints, im planning to switch to C#.

---

### Post by Jimmey on 2006-05-04
From what I can gather, it's the cross platform compatability issues that deal VB the greatest blow. Visual Basic's alternatives ( which, to my mind, include the C family ) are usually able to compile for mutliple platforms. And the fact that Visual Basic is only available for an closed-source operating system means that it can never be used to the same extent a language like C can with Linux.

---

### Post by scooper on 2006-05-04
.NET is ok.  The toolset from MS has fallen behind Eclipse and other Java environments.  I think VB.NET is considered somewhat of an orphan, and doesn't add much value over C#, which is generally a better language IMO.

All the .NET languages are basically "syntax skins" on top of the same interpreter.  I'd go with the best-supported, which is currently C#.  For a clone (I assume you'd use Mono?) I would guess it's even more likely that they'd focus their energies supporting the most popular and mainstream MS language.

Hope that helps
Steve

---

### Post by unbuntu on 2006-05-04
[QUOTE=drpolish]It's such an easy language to use, but it isn't cross-platform. But what are your other gripes on VB? VB.NET? Because of all these complaints, im planning to switch to C#.[/QUOTE]

Under .NET VB and C# are almost the same.  (If you take a look at any ASP.NET code, either written in VB.NET or C#, you'll find they are amazingly similar, which almost makes .NET's goal - make programmers program in their favorite languages and achieve the same thing- look void since VB.NET changed so much from the previous version, and it's even easier for VB programmers to learn C# instead of VB.NET)

But the point I'm not so fond of VB is it's syntax.  Call me superficial, but I just find that writing "{}" is easier and clearer than "blah blah...end blah" and so many other such instances.  Also, for VB to run on Windows you have to get a big (well, for the computers of that age anyway) runtime library whereas the libraries to run MFC programs are already included upon installation.  Anyway, that could hardly be an objection to VB since now if you don't have .NET runtime installed you still have to get it no matter VB.NET or C# your program is written in.

---

### Post by cwaldbieser on 2006-05-05
[QUOTE=drpolish]It's such an easy language to use, but it isn't cross-platform. But what are your other gripes on VB? VB.NET? Because of all these complaints, im planning to switch to C#.[/QUOTE]
Things I hate about VB 6:
+ The IDE is ultra annoying.  It doesn't like to let you leave a line syntactically incorrect for even a second without sqwaking at you.
+ There is a limit to the number of line continuations you can have which can sometimes be pretty annoying.
+ The language has very limited support for user defined data structures.  You can declare something similar to a struct in C, but it's utility is somewhat limited.
+ I never enjoyed having to differentiate between a Sub and a Function.  The calling syntax is even more annoying (when to use parentheses).
+ The way you return a value from a function is syntactically unpleasing to me-- I like RETURN statements a lot better.
+ No BREAK or CONTINUE in loops.
+ You need to add line numbers to your code to find out what line an error occured on.

VB.Net is a big improvement, though I still don't really take much of a shine to the syntax.  It still seems too wordy to me in some respects.  There are still some things I don't really care for, but I am a relative newcomer, so I may just be using the tool in the wrong way:
+ Still no CONTINUE in VS 2003- I heard this feature was added in VS 2005, though?
+ Still don't like differentiating between a Sub vs. Function.
+ I find creation of composite data types more natural, but I have already observed where overuse of lots of small structs can bite you.  A coworker was creating a lot of small structs to pass data in a loop that repeated millions of times.  Apparently, the garbage collector was feeling a bit lazy, because the creation of these small structs started eating up all the RAM on my system when I tested his app out.  It took me a little while to track down the cause.  I found that implementing IDispose on each of the structs and calling it manually dramatically improved the situation.  I had thought the whole point of the GC was so I didn't have to worry about explicit memory management.

---

### Post by RavenOfOdin on 2006-05-05
My beefs with VB6 are as follows:

Event driven.
Programs compiled require unnecessary, and often many, .DLL/.OCX files.
Closed source.
Syntax is horrible.

---

### Post by LordHunter317 on 2006-05-05
> **drpolish]It's such an easy language to use, but it isn't cross-platform. But what are your other gripes on VB?[/quote]The syntax is terrible and the language has lots of painful limitations.

> VB.NET?The syntax is too verbose and the compiler is buggy with no good reason.  Also the Intellisense in VS 2K5 is inferior to the C# editor's.

[quote=Jimmey]From what I can gather, it's the cross platform compatability issues that deal VB the greatest blow.[/quote]As some point, Mono intends to do a visual basic compiler.  While the language isn't an ECMA standard like C#, there's actually not a ton of stuff to engineer.  Most of it's different semantics are well known and stuffed in Microsoft.VisualBasic.dll.  There is some stuff that is compiler internal, but it's obvious stuff, you'd just have to write it's implementation. (Hint: you have to do that anyway, so it's no loss).

[quote=scooper]I think VB.NET is considered somewhat of an orphan, and doesn't add much value over C#, which is generally a better language IMO.[/quote]No, it hasn't.  It's fully supported and will be forever, probably.  It has distinct advantages over C# in some situations, specifically when dealing with COM Interop.

> All the .NET languages are basically "syntax skins" on top of the same interpreter. I'd go with the best-supported, which is currently C#.Even if it's just syntax, which isn't actually true, that's a  major difference.  See Boo or Nemerle for good examples of this.

[quote=cwaldbieser]+ The way you return a value from a function is syntactically unpleasing to me-- I like RETURN statements a lot better.[/quote]VB.NET has this, thankfully.  VB6 was really crying for a functional return style: whatever the result of the last expression was is the value returned.  Only, that would be too confusing for the intended audience.

> + I find creation of composite data types more natural, but I have already observed where overuse of lots of small structs can bite you.Of course it can, they're allocated on the stack.  Too many structs and you'll blow the bottom of the stack out.  Do you mean class?  A class is a reference^W pointer UDT, a struct is a value UDT.  The former is always allocated on the heap and is GC'd said:**
> Apparently, the garbage collector was feeling a bit lazy, because the creation of these small structs started eating up all the RAM on my system when I tested his app out.The .NET GC is still not perfect and occasionally doesn't collect as optimistically as one might think it should.

> I found that implementing IDispose on each of the structs and calling it manually dramatically improved the situation.This doesn't make any sense.  Even if it were a class, implementing IDispose won't help anything unless you have unmanaged resources to clean up.  Now if it did need to and didn't previously, that would create the behavior you're seeing.  Why?  Because objects with finalizers are only collected in the last generation.

Even more importantly, if they were really structs and needed to be finalized, you were leaking resources like a sieve.  Structs are never finalized, period.  The lesson here is that if you need to implement IDispose, your object had better be a class.  The GC expects as much.

>  I had thought the whole point of the GC was so I didn't have to worry about explicit memory management.Memory?  No.  Resources? Yes.

[quote=RavenOfOdin]
Event driven.[/quote]Which makes sense for a GUI environment.  All GUI APIs are event-driven, even the ancient C ones.

> Programs compiled require unnecessary, and often many, .DLL/.OCX files.If it required it to run, it's obviously not unnecessary.

---

### Post by mostwanted on 2006-05-05
^ Actually, there already is a vb.net compiler for Mono. It's called mbs.

---

### Post by cwaldbieser on 2006-05-06
[QUOTE=LordHunter317]
This doesn't make any sense.  Even if it were a class, implementing IDispose won't help anything unless you have unmanaged resources to clean up.  Now if it did need to and didn't previously, that would create the behavior you're seeing.  Why?  Because objects with finalizers are only collected in the last generation.

Even more importantly, if they were really structs and needed to be finalized, you were leaking resources like a sieve.  Structs are never finalized, period.  The lesson here is that if you need to implement IDispose, your object had better be a class.  The GC expects as much.
[/QUOTE]
Well, my terminology is somewhat imprecise.  You are correct, it is a class that was being created on the heap, but the fellow who wrote the program was using it the way I'd use a struct in C++.  He is basically just sticking a bunch of related data fields together and passing them around as a unit.  The class only appears to have data members that are simple types (Integers, Strings, a Date), so it is not clear to me what kind of resource could be leaked.

I am less the theorist and more the experimentalist.  All I can say is what I observed.  The longer the program ran, the more memory it consumed.  This particular class was being created repeatedly in a pretty tight loop.  Once I added the call to Dispose(), the memory consumption plataued and stayed at a relatively constant level no matter how long I let the program run.

If you have any ideas why this happened, I'd be glad to hear them.  The class is included below.  I doctored it up a little since I can't really post company code verbatim on the Internet, but the structure is essentially the same.  The loop it was in looked something like:
```

whlie not finished
     'Read some data
     Dim data_glob As New DataGlob(x,y,z,a,b,c)                                                                
     'Other processing
     'Call to Dispose() inserted at this point- problem goes away.  Why?
end while

```

```

Option Explicit On 
Option Strict On

Imports System
Imports System.Data
Imports System.Data.OleDb
Imports System.Data.SqlClient
Imports System.Data.Odbc

#If DEBUG Then
Imports System.Diagnostics
#End If

Imports System.IO

Public Class DataGlob
    Inherits SQLServerDataObject
    Implements IDisposable

#Region "  DataGlob Class Constant Definitions  "

    Private Const SQL_INSERT_COMMAND_FORMAT As String = _
    "INSERT INTO mr_stu_marks (district, student_id, section_key, " & _
    "course_session, marking_period, mark_type, mark_value, override, " & _
    "change_date_time, change_uid) VALUES ({0}, '{1}', {2}, {3}, '{4}'," & _
    "'{5}', '{6}', '{7}', '{8}', '{9}')"


    Private Const BULK_INSERT_DATA_FORMAT As String = _
    "{0}" & vbTab & "{1}" & vbTab & "{2}" & vbTab & "{3}" & vbTab & _
    "{4}" & vbTab & "{5}" & vbTab & "{6}" & vbTab & "{7}" & vbTab & _
    "{8}" & vbTab & "{9}"

    Private Const DATA_TRACE_FORMAT As String = _
    "District ID: {0}" & vbCrLf & "Student ID: {1}" & vbCrLf & _
    "Section Key: {2}" & vbCrLf & "Course Session: {3}" & vbCrLf & _
    "Marking Period: {4}" & vbCrLf & "Mark Type: {5}" & vbCrLf & _
    "Mark Value: {6}" & vbCrLf & "Override: {7}" & vbCrLf & _
    "Change Date: {8}" & vbCrLf & "Change UID: {9}"

    Private Const INVALID_SOURCE_GRADE_VALUE As String = _
    "ERROR: StudentPlus Grade Type {0} not set for Student ID {1} " & _
    "in Course {2}, Session {3} and Marking Period {4} for School Year {5}"

#End Region

#Region "  DataGlob Class Data Members  "

    Private theDistrict As Integer
    Private theStudentID As String
    Private theSectionKey As Integer
    Private theCourseSession As Integer
    Private theMarkingPeriod As String
    Private theMarkType As String
    Private theMarkValue As String
    Private theOverride As String
    Private theChangeDateTime As DateTime
    Private theChangeUID As String

#End Region

#Region "  DataGlob Constructors & Destructor  "

    Public Sub New(ByVal courseMarks As StudentPlusCourseMarks, _
                    ByVal gradeInstance As CourseGradeInstance, _
                    ByVal gradeType As String, _
                    ByVal districtID As Integer, _
                    ByVal sectionKey As Integer, _
                    ByVal changeUID As String)

        If courseMarks Is Nothing Then
            Throw New ArgumentNullException("courseMarks")
        End If

        If gradeType = String.Empty Then
            Throw New ArgumentNullException("gradeType")
        End If

        If districtID < 0 Then
            Throw New ArgumentException("districtID")
        End If

        If changeUID = String.Empty Then
            Throw New ArgumentNullException("changeUID")
        End If

        theDistrict = districtID
        theStudentID = courseMarks.StudentID.ToString()
        theSectionKey = sectionKey
        theCourseSession = courseMarks.Session
        theMarkingPeriod = courseMarks.MarkingPeriod
        theMarkType = gradeType

        If courseMarks.IsValidGrade(gradeInstance) = False Then
            Dim gradeInstanceName As String = gradeInstance.ToString()

            Dim invalidGradeInstance As String = String.Format( _
            INVALID_SOURCE_GRADE_VALUE, theStudentID, courseMarks.Course(), _
            theCourseSession.ToString(), theMarkingPeriod, _
            courseMarks.SchoolYear.ToString())

            Throw New ArgumentException(invalidGradeInstance)
        End If

        Select Case gradeInstance.Type
            Case CourseGradeInstance.GradeType.Grade1
                theMarkValue = courseMarks.Grade1
                theOverride = courseMarks.Grade1Override

            Case CourseGradeInstance.GradeType.Grade2
                theMarkValue = courseMarks.Grade2
                theOverride = courseMarks.Grade2Override

            Case CourseGradeInstance.GradeType.Grade3
                theMarkValue = courseMarks.Grade3
                theOverride = courseMarks.Grade3Override

            Case CourseGradeInstance.GradeType.FinalGrade
                theMarkValue = courseMarks.FinalGrade
                theOverride = courseMarks.FinalGradeOverride
        End Select

        theChangeUID = changeUID
        theChangeDateTime = DateTime.Now()
    End Sub

    Protected Overridable Overloads Sub Dispose(ByVal disposing As Boolean)
        If disposing Then
            theStudentID = String.Empty
            theMarkingPeriod = String.Empty
            theMarkType = String.Empty
            theMarkValue = String.Empty
            theOverride = String.Empty
            theChangeUID = String.Empty
            theChangeDateTime = Nothing
        End If
    End Sub

    Public Overloads Sub Dispose() Implements IDisposable.Dispose
        Dispose(True)
        GC.SuppressFinalize(Me)
    End Sub

    Protected Overrides Sub Finalize()
        Dispose(False)
    End Sub

#End Region

#Region "  DataGlob Property Accessors  "

    Public ReadOnly Property District() As Integer
        Get
            Return theDistrict
        End Get
    End Property

    Public ReadOnly Property StudentID() As String
        Get
            Return theStudentID
        End Get
    End Property

    Public ReadOnly Property SectionKey() As Integer
        Get
            Return theSectionKey
        End Get
    End Property

    Public ReadOnly Property CourseSession() As Integer
        Get
            Return theCourseSession
        End Get
    End Property

    Public ReadOnly Property MarkingPeriod() As String
        Get
            Return theMarkingPeriod
        End Get
    End Property

    Public ReadOnly Property MarkType() As String
        Get
            Return theMarkType
        End Get
    End Property

    Public ReadOnly Property MarkValue() As String
        Get
            Return theMarkValue
        End Get
    End Property

    Public ReadOnly Property Override() As String
        Get
            Return theOverride
        End Get
    End Property

    Public ReadOnly Property ChangeUID() As String
        Get
            Return theChangeUID
        End Get
    End Property

    Public ReadOnly Property ChangeDateTime() As DateTime
        Get
            Return theChangeDateTime
        End Get
    End Property

#End Region

#Region "  DataGlob Class Implementation  "

    Public Overrides Function SQLInsertCommand() As String
        Dim sqlStatement As String = String.Format(SQL_INSERT_COMMAND_FORMAT, _
        theDistrict.ToString(), theStudentID, theSectionKey.ToString(), _
        theCourseSession.ToString(), theMarkingPeriod, theMarkType, _
        theMarkValue, theOverride, theChangeDateTime.ToString(), theChangeUID)

        Return sqlStatement
    End Function

    Public Overrides Function BulkInsertRecord() As String
        Dim bulkData As String = _
        String.Format(BULK_INSERT_DATA_FORMAT, theDistrict.ToString(), _
        theStudentID.Trim(), theSectionKey.ToString(), _
        theCourseSession.ToString(), theMarkingPeriod.Trim(), _
        theMarkType.Trim(), theMarkValue.Trim(), theOverride.Trim(), _
        theChangeDateTime.ToString().Trim(), theChangeUID.Trim())

        Return bulkData
    End Function

    Overrides Function ToString() As String
        Dim dataTrace As String = String.Format(DATA_TRACE_FORMAT, _
        theDistrict.ToString(), theStudentID, theSectionKey.ToString(), _
        theCourseSession.ToString(), theMarkingPeriod, theMarkType, _
        theMarkValue, theOverride, theChangeDateTime.ToString(), theChangeUID)

        Return dataTrace
    End Function

#End Region

End Class

```

---

### Post by LordHunter317 on 2006-05-06
The only possible reason why is if a finalizer was always defined for the class.  There clearly shouldn't be one, nor any reason for the class to implement IDisposable.  What statistics were you tracking specifically and far more importantly, how?

---

### Post by cwaldbieser on 2006-05-06
[QUOTE=LordHunter317]The only possible reason why is if a finalizer was always defined for the class.  There clearly shouldn't be one, nor any reason for the class to implement IDisposable.  What statistics were you tracking specifically and far more importantly, how?[/QUOTE]
There is a utility I got from [www.systeminternals.com](www.systeminternals.com) called process explorer, which is somewhat like Windows task manager.  The program is a console app.  I fire it up, bring up process explorer, click on the process image and I can see statistics for the process plus a real-time graph of its CPU usage and memory consumption.  The memory graph just kept going up and up.  I normally record the "Peak Private Bytes" element from the performance tab.

I can go back in the source history and check if the class always had a finalizer.  What exactly would happen if it had one but was never explicitly being called?

---

### Post by LordHunter317 on 2006-05-07
[QUOTE=cwaldbieser]I can go back in the source history and check if the class always had a finalizer.  What exactly would happen if it had one but was never explicitly being called?[/QUOTE]If you never explictly suppressed finalization, then you would force all those objects to be reaped in the last generation.  Only the last generation runs finalizers.

The other possible problem is that if the loop was tight enough, you weren't pausing long enough to allow the GC to collect anything.  The GC doesn't run in parallel in workstation mode.  The addition of the Dispose() call (btw, you should use using statements) may have given it enough breathing room to collect.  Adding specific pauses for teh GC or explict cleanup calls could maybe solve it.

---

