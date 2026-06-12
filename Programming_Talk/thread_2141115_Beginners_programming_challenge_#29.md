---
title: "Beginners programming challenge #29"
date: 2013-05-01
forum: Programming Talk
---

### Post by BluNova on 2013-05-01
It has been 6 months since #28 so I decided to put my rarely-used ubuntu forums account to good use and create #29!
[U][SIZE=4][COLOR=Red]We welcome you to the 29th Beginners programming challenge!

[/COLOR][/SIZE][/U]The task is simple, create a converter between the [Gregorian Calendar]("http://en.wikipedia.org/wiki/Gregorian_calendar") and the disused [French Revolutionary Calendar]("http://en.wikipedia.org/wiki/French_Revolutionary_Calendar")

It only has to convert from Gregorian to French Revolutionary
It should take input in the following formats:
1) Through a command line interface through this format (<program name> -i)
2) Through a file printing the output through the screen in this format (<program name> <file name>)
3) Through a file exporting the output to another format through this format (<program name> <file name> -o <output file name>)

[COLOR=#000000][COLOR=#000000]*[FONT=sans-serif]A fixed arithmetic rule for determining leap years was proposed in the name of the Committee of Public Education by [/FONT]*[/COLOR][/COLOR][Gilbert Romme]("http://en.wikipedia.org/wiki/Gilbert_Romme")[COLOR=#000000][COLOR=#000000]*[FONT=sans-serif] on 19 Floréal An III (8 May 1795). The proposed rule was to determine leap years by applying the rules of the Gregorian calendar to the years of the French Republic (years IV, VIII, XII, etc. were to be leap years) except that year 4000 (the last year of ten 400-year periods) should be a common year instead of a leap year.[/FONT]*[/COLOR][/COLOR]
When entering the date into the program it should accept the following format **Decade (I/II/III), (day) de (month) de l'Annee (year) de la Revolution** or **La Fete (<COMPLEMENTARY DAY: [look here]("http://en.wikipedia.org/wiki/French_Republican_Calendar#Complementary_days")>) de l'Annee (year) de la Revolution**
[U]Cookie Points
[/U]1) Export the year in roman numerals
2) Convert both ways

_**Disqualified Entries**_

[COLOR=#000000]Any overly obfuscated code will be immediately disqualified without account for programmers skill. Please remember that these challenges are for beginners and therefore the code should be easily readable and well commented.[/COLOR]

[COLOR=#000000]Any non-beginner entries will not be judged. Please use common sense when posting code examples. Please do not give beginners a copy paste solution before they have had a chance to try this for themselves.
[B][U]
Assistance 
[/U][/B]If you need help feel free to ask around on irc.freenode.net channel #ubuntu-beginners-dev
[/COLOR]

---

### Post by Iowan on 2013-05-14
It's BACK!

---

### Post by Leuchten on 2013-05-15
This actually seems like a non-beginners challenge since the French Revolutionary calendar officially begins on the true autumnal equinox. Can the fixed rule described in the wikipedia article be used? 

> [COLOR=#000000][FONT=sans-serif]A fixed arithmetic rule for determining leap years was proposed in the name of the Committee of Public Education by [/FONT][/COLOR][Gilbert Romme]("http://en.wikipedia.org/wiki/Gilbert_Romme")[COLOR=#000000][FONT=sans-serif] on 19 Floréal An III (8 May 1795). The proposed rule was to determine leap years by applying the rules of the Gregorian calendar to the years of the French Republic (years IV, VIII, XII, etc. were to be leap years) except that year 4000 (the last year of ten 400-year periods) should be a common year instead of a leap year.[/FONT][/COLOR]

---

### Post by ofnuts on 2013-05-15
If you look at the [French Wikipedia](https://fr.wikipedia.org/wiki/Calendrier_r%C3%A9publicain#Post.C3.A9rit.C3.A9), there are divergent opinions about the extension of the calendar outside its 14 years of actual use... Looks like there should be an option parameter :)

---

### Post by Leuchten on 2013-05-15
Also, how do you enter the sans-culottides with the format **Decade (I/II/III), (jour) de (mois) de l'Annee (année) de la Revolution.**?

---

### Post by BluNova on 2013-05-15
I have changed it to this rule for leap years:

[COLOR=#000000][COLOR=#000000]*[FONT=sans-serif]A fixed arithmetic rule for determining leap years was proposed in the name of the Committee of Public Education by [/FONT]*[/COLOR][/COLOR][Gilbert Romme]("http://en.wikipedia.org/wiki/Gilbert_Romme")[COLOR=#000000][COLOR=#000000]*[FONT=sans-serif] on 19 Floréal An III (8 May 1795). The proposed rule was to determine leap years by applying the rules of the Gregorian calendar to the years of the French Republic (years IV, VIII, XII, etc. were to be leap years) except that year 4000 (the last year of ten 400-year periods) should be a common year instead of a leap year.[/FONT]*[/COLOR][/COLOR]

---

### Post by alan9800 on 2013-05-17
> **BluNova said:**
> I have changed it to this rule for leap years:

[COLOR=#000000][COLOR=#000000]*[FONT=sans-serif]A fixed arithmetic rule for determining leap years was proposed in the name of the Committee of Public Education by [/FONT]*[/COLOR][/COLOR][Gilbert Romme]("http://en.wikipedia.org/wiki/Gilbert_Romme")[COLOR=#000000][COLOR=#000000]*[FONT=sans-serif] on 19 Floréal An III (8 May 1795). The proposed rule was to determine leap years by applying the rules of the Gregorian calendar to the years of the French Republic (years IV, VIII, XII, etc. were to be leap years) except that year 4000 (the last year of ten 400-year periods) should be a common year instead of a leap year.[/FONT]*[/COLOR][/COLOR]If I have rightly understood this rule, the leap_year function could be written as follows:```
def leap_year(yr)
    return (((yr.remainder(4)==0) and (yr.remainder(100)!=0)) or ((yr.remainder(400)==0) and ((yr / 400)!=10)))
end
```

---

### Post by BluNova on 2013-05-17
I don't think so, as 100 would not be a leap year on your function
You could easily do it by checking that its divisible by 4 and then checking that the year is not 4000

---

### Post by trent.josephsen on 2013-05-17
Years divisible by 100 but not by 400 are not leap years in the Gregorian calendar; this confusion is the source of one [somewhat notorious bug](https://en.wikipedia.org/wiki/Year_1900_problem) in Microsoft Excel. But I read it as meaning that *every* 4000th year is a common year. So I'd tweak alan9800's algorithm to be
```
def leap_year(y)
    (4 divides y) and (100 does not divide y) or (400 divides y) and (4000 does not divide y)
```

You basically have to write out the whole truth table to verify it, though. Maybe there's a clearer way.

---

### Post by alan9800 on 2013-05-18
> **BluNova said:**
> I don't think so, as 100 would not be a leap year on your function
You could easily do it by checking that its divisible by 4 and then checking that the year is not 4000as trent.josephsen has explained in the above post, according to the rules of the Gregorian calendar not all the years which are divisible by 100 are leap years, but only those which are divisible by 400.
This said, I'd have a question: should I consider as a normal year only the year 4000 or even its multiples, e.g. the years 8000, 12000 and so on? I ask this because, at least by reading what's written on wikipedia,  it's not clear if the rule of Romme has to be applied only to the year 4000 or even to its multiples.

---

### Post by shawnhcorey on 2013-05-18
I'm assuming you mean the Gregorian Calendar in France, which was adopted in 1582, not England's (and America's) of 1752.

---

### Post by trent.josephsen on 2013-05-18
Either way, there is no obvious way to extend the Republican calendar proleptically before 1792, so I think the best solution for earlier dates is probably to just throw an error. This is a *beginner's* challenge after all.

---

### Post by shawnhcorey on 2013-05-18
> **trent.josephsen said:**
> Either way, there is no obvious way to extend the Republican calendar proleptically before 1792, so I think the best solution for earlier dates is probably to just throw an error. This is a *beginner's* challenge after all.

It seems to me that the hardest part of this challenge is figuring out the policy the program should follow and not the code.

---

### Post by trent.josephsen on 2013-05-18
So, a great example of real-world problem solving? :)

There are a few wrinkles but I don't think it's a bad challenge overall.

---

### Post by BluNova on 2013-05-19
I would say that there is no requirement to extend dates backwards past the first year of the revolutionary calendar as there was never any way of determining how this would apply
Also i mean England's and America's Gregorian Calendar i.e the current one

---

### Post by alan9800 on 2013-05-20
> **trent.josephsen said:**
> Years divisible by 100 but not by 400 are not leap years in the Gregorian calendar; this confusion is the source of one [somewhat notorious bug]("https://en.wikipedia.org/wiki/Year_1900_problem") in Microsoft Excel. But I read it as meaning that *every* 4000th year is a common year. So I'd tweak alan9800's algorithm to be
```
def leap_year(y)
    (4 divides y) and (100 does not divide y) or (400 divides y) and (4000 does not divide y)
```

You basically have to write out the whole truth table to verify it, though. Maybe there's a clearer way.if this is the meaning of the rule, then the function may be rewritten as follows:```
def leap_year(yr)
    return (((yr.remainder(4)==0) and (yr.remainder(100)!=0)) or ((yr.remainder(400)==0) and (yr.remainder(4000)!=0)))
end
```

---

### Post by trent.josephsen on 2013-05-20
Was my pseudocode not good enough for you? :P

---

### Post by alan9800 on 2013-05-20
> **trent.josephsen said:**
> Was my pseudocode not good enough for you? :Pyour code was surely good, it's the interpretation of the rule which is quite unclear.
I'm still waiting for knowing if it's only the year 4000 to not be leap according to the above rule or even its multiples.

---

### Post by BluNova on 2013-05-23
if its a multiple of 100 and not 400, or its a multiple of 4000 its not a leap year

---

### Post by Leuchten on 2013-06-09
Since it's been a month since this has been posted and there are no other entries, I'll go ahead and post mine.

```
import java.io.{FileWriter, BufferedWriter}
import scala.io.Source


object DateUtil {
  def isLeapYear(y: Int) = y % 4 == 0 && y % 100 != 0 || y % 400 == 0


  def gregorianMonthLengths(y: Int) = List(31, 28 + (if(isLeapYear(y)) 1 else 0), 31, 30, 31, 30, 31, 31, 30, 31, 30, 31)
}

object FRDate {
  //for some reason, after 1992 and before the 1800s the new year is the 12th of nivose, not the 11th. Also, on the years 1804 and 1808, the gregorian new year was on the 10th of nivose.
  def gregorianNewYear(a: Int) = if(a == 1804 || a == 1808) FRDate(10,04,a-1792) else if(a > 1992 || a < 1800) FRDate(12,04,a-1792) else FRDate(11,04,a-1792)


  //converts unicode characters into non-unicode ones
  private def deUnicode(c: Char) = {
    c.toLower match {
      case 'é'|'ê' => 'e'
      case 'ô' => 'o'
      case x => x
    }
  }




  //An extension method class for ints, all ints now have a romanize function that turns them into a roman numeral
  implicit class RomanInts(val i: Int) extends AnyVal {


    private def romanize(level: Int, ones: String, fives: String, tens: String) = {
      val s = ((i / level) % 10) match {
        case 4 => ones + fives
        case x if x > 4 & x < 9 => fives
        case 9 => ones + tens
        case _ => ""
      }
      s + (ones*((i / level) % 10 % 5 % 4))
    }


    def toRomanNumeral = "M" * (i / 1000) + romanize(100, "C", "D", "M") + romanize(10, "X", "L", "C") + romanize(1, "I", "V", "X")
  }


  //used to match for input parsing, as well as pretty printing the date
  val monthMap = IndexedSeq("Vendémiaire", "Brumaire", "Frimaire",
    "Nivôse", "Pluviôse", "Ventôse",
    "Germinal", "Floréal", "Prairial",
    "Messidor", "Thermidor", "Fructidor", "Sans-culottide")


  //lazy values are only calculated when they are needed, these won't be calculated until the parser tries to parse ascii versions of the month
  lazy val nonUnicodeMonthMap = monthMap map (_ map (deUnicode))


  val dayMap = IndexedSeq("Primidi", "Duodi", "Tridi", "Quartidi", "Quintidi", "Sextidi", "Septidi", "Octidi", "Nonidi", "Décadi")


  lazy val nonUnicodeDayMap = dayMap map (_ map (deUnicode))


  //days for the "13th" month
  val sansCulottides = IndexedSeq("La Fête de la Vertu", "La Fête du Génie", "La Fête du Travail", "La Fête de l'Opinion",
    "La Fête des Récompenses", "La Fête de la Revolution")


  lazy val nonUnicodeSansCulottides = sansCulottides map (_ map (deUnicode))


  //checks both unicode and non-unicode versions of the months, followed by an attempt to parse a roman numeral
  // => IndexedSeq[String] means that it doesn't evaluate the argument until it's used in the function. This is to keep lazy vals such as nonUnicodeMonthMap from being calculated until absolutely necessary.
  private def getIndexOrConvertNumeral(s: String, nuL: => IndexedSeq[String], l: => IndexedSeq[String]) = {
    (l.map(_.toLowerCase).indexOf(s.toLowerCase) match {
      case -1 => nuL.indexOf(s.toLowerCase)
      case i => i
    }) match {
      case -1 => s match {
        case romanRegex(s) => fromRomanNumeral(s)
        case _ => throw new Exception("String doesn't match any form of valid input!")
      }
      case i => i + 1
    }
  }


  //takes a string matching the format of either regex.
  def parse(s: String) = {
    val regex = """D[eé]cade\s+([MCDXLIV]*),\s*(\p{L}+|[XVI]+)\s+de\s+(\p{L}+|[XVI]+)\s+de\s+l'Ann[ée]e\s+([MCDXLIV]+)\s+de\s+la\s+R[ée]volution\.?""".r
    val sCulottRegex = """(La F[êe]te .+)\s+de\s+l'Ann[ée]e\s+([MCDXLIV]+)\s+de\s+la\s+R[ée]volution""".r
    s match {
      case regex(dec, jour, mois, annee) => {
        val week = if(dec.isEmpty) 0 else fromRomanNumeral(dec)
        val day = getIndexOrConvertNumeral(jour, nonUnicodeDayMap, dayMap)
        val month = getIndexOrConvertNumeral(mois, nonUnicodeMonthMap, monthMap)
        val year = fromRomanNumeral(annee)


        FRDate(day+ (week - 1) * 10, month, year)
      }
      case sCulottRegex(jour, annee) => {
        val day = (sansCulottides map (_.toLowerCase) indexOf (jour.toLowerCase) match {
          case -1 => nonUnicodeSansCulottides map (_.toLowerCase) indexOf (jour.toLowerCase)
          case i => i
        }) match {
          case -1 => throw new Exception("String doesn't match any form of valid input!")
          case i => i + 1
        }


        val year = fromRomanNumeral(annee)


        FRDate(day, 13, year)
      }
      case _ => throw new Exception("Invalid date!!")
    }


  }


  //converts a roman numeral into an int
  private def fromRomanNumeral(s: String) = {
    val startCount = s.count(_ == 'M')*1000 + s.count(_ == 'C')*100 + s.count(_ == 'D')*500 +
      s.count(_ == 'X') * 10 + s.count(_ == 'L') * 50 + s.count(_ == 'V') * 5 + s.count(_ == 'I') * 1


    //turns a string like "abc" into a list like List(('a','b'),('b','c'))
    val pairs = s zip s.tail


    //removes the extra stuff added by startcount interpreting things like IV as 6
    startCount - pairs.count{case (a,b) => a == 'I' && (b == 'X' || b == 'V')} * 2 -
      pairs.count{case (a,b) => a == 'X' && (b == 'L' || b == 'C')} * 20 -
      pairs.count{case (a,b) => a == 'C' && (b == 'D' || b == 'M')} * 200
  }


  val romanRegex = """([MCDXLIV]+)""".r


  //takes a date of DD/MM/YYYY gregorian format and makes it into a FRDate.
  def fromGregorianDate(d: Int, m: Int, y: Int) = {
    val newYear = gregorianNewYear(y)
    //days since 1/4/y in the French Revolutionary Calendar
    val days = ((m-1,0) /: DateUtil.gregorianMonthLengths(y)) {case ((remMonths, totalDays), daysInMonth) => if(remMonths > 0) (remMonths-1, totalDays + daysInMonth) else (0, totalDays)}._2 + (d-1)


    val moisPt1 = 4 + ((days + newYear.jour - 1)/30)


    val frNewYearPassed = moisPt1 > 13 || moisPt1 == 13 && (days+newYear.jour) % 30 > (if(DateUtil.isLeapYear(y)) 6 else 5)


    //if the number of months reported by moisPt1 is 13 and the numbers of days in the month is greater than 6 or 5
    // (depending on whether or not it's a leap year), remove the gregorianNewYear - French revolutionary new year of
    // the next year days from days to make adjusted days, otherwise, adjusted days == days
    val adjustedDays = if(frNewYearPassed) days - FRDate(01,01, y+1-1792).daysBetween(newYear) else days + newYear.jour - 1


    // calculation of the day of the month in the french calendar
    val jour = adjustedDays % 30 + 1


    //calculation of the month of the year in the french calendar
    val mois = if(frNewYearPassed) adjustedDays / 30 + 1 else moisPt1


    //calculation of the year in the french calendar
    val année = y - 1792 + (if(frNewYearPassed) 1 else 0)




    FRDate(jour,mois,année)
  }
}


//A date on the French revolutionary calendar
// jour, mois, and année are the french words for day, month, and year
case class FRDate(jour: Int, mois: Int, année: Int) {
  require(jour <= 30 && jour >= 1, s"day out of range: $jour")
  require(mois <= 13 && mois >= 1, "month out of range")
  require(année >= 1, s"year before 1: $année")


  import FRDate.RomanInts




  // lazy values are not calculated until requested.
  lazy val leapYear = DateUtil.isLeapYear(année)


  lazy val leapDay: Option[FRDate] = if(leapYear) Some(FRDate(06, 13, année)) else None


  lazy val gregorianNewYear = FRDate.gregorianNewYear(année+1792)


  def avecAnnée(a: Int) = FRDate(jour, mois, a)


  def avecMois(m: Int) = FRDate(jour, m, année)


  def avecJour(j: Int) = FRDate(j, mois, année)


  //used to determine if one date is before another
  def before(other: FRDate) = if(année < other.année) true else if (année == other.année) {
    if(mois < other.mois) true else if (mois == other.mois) {
      if(jour < other.jour) true else false
    } else false
  } else false


  //calculates the number of days between two dates
  def daysBetween(other: FRDate) = {
    //calculates the number of days from years between these dates. if there is no difference in year, this returns the calculated day difference
    def dayHelper(m: FRDate, s: FRDate): Int = {
      if(m.année != s.année) 365 + (if(m.leapYear) 1 else 0) + dayHelper(m avecAnnée(m.année - 1), s)
      else _monthAdjuster(m,s) + _dayAdjuster(m avecMois s.mois, s)
    }


    //calculates the days from months
    def _monthAdjuster(m: FRDate, s: FRDate): Int = m.mois * 30 - s.mois * 30


    def _dayAdjuster(m: FRDate, s: FRDate): Int = m.jour - s.jour


    val (m,s) = if(this before other) (other, this) else (this, other)


    dayHelper(m,s) - (m.leapDay map (lD => if((m before lD) && s.année - m.année >= 1) 1 else 0) getOrElse(0))
  }


  //the year of this FRDate in the gregorian calendar
  lazy val gregorianYear = 1791 + année + (if(this before gregorianNewYear) 0 else 1)




  //the month of this FRDate in the gregorian calendar
  lazy val gregorianMonth = {
    val refPoint = if(this before gregorianNewYear) gregorianNewYear avecAnnée(année - 1) else gregorianNewYear


    val daysSince = (refPoint daysBetween this) + 1


    val m = DateUtil.gregorianMonthLengths(gregorianYear)


    (m foldLeft (0 -> daysSince)) {case (tup, days) => (tup._1 + (if(tup._2 > 0) 1 else 0), tup._2 - days) }._1
  }


  //the day of this FRDate in the gregorian calendar
  lazy val gregorianDay = {
    val refPoint = if(this before gregorianNewYear) gregorianNewYear avecAnnée(année - 1) else gregorianNewYear


    val daysSince = (refPoint daysBetween this) + 1


    (DateUtil.gregorianMonthLengths(gregorianYear).take(gregorianMonth - 1) foldLeft daysSince) (_-_)
  }


  def gregorianDateString = s"$gregorianDay/$gregorianMonth/$gregorianYear"


  override def toString = if(mois != 13)
    s"Décade ${((jour - 1)/ 10 + 1).toRomanNumeral}, ${FRDate.dayMap((jour - 1) % 10)} de ${FRDate.monthMap(mois-1)} de l'Année ${année.toRomanNumeral} de la Révolution"
  else
    s"${FRDate.sansCulottides(jour - 1)} de l'Année ${année.toRomanNumeral} de la Révolution"
}

object Cal {


  def main(args: Array[String]) {


    //converts either gregorian dates of the format DD/MM/YYYY or french republic dates of the format listed in the challenge into the corresponding French republic date or Gregorian date
    def interpreter(l: String) = {
      val r = """\s*([0-3]?\d)/([01]?\d)/(\d{4})""".r
      l match {
        case "exit" => System.exit(0); ???  //??? is there as a return type of Nothing. If it's accessed, an error will occur, which shouldn't happen because the program should have exited already
        case r(day,month,year) => try {
          FRDate.fromGregorianDate(day.toInt,month.toInt,year.toInt).toString
        } catch { case e: Exception => e.getMessage }
        case _ => try {
          FRDate.parse(l).gregorianDateString
        }
      }
    }


    args match {
      case Array("-i") => {
        Source.fromInputStream(System.in)(io.Codec.UTF8).getLines() foreach {l => println(interpreter(l))}
      }
      case Array(file) => Source.fromFile(file)(io.Codec.UTF8).getLines() foreach {l => println(interpreter(l))}
      case Array(file, "-o", outFile) => {
        val res = Source.fromFile(file)(io.Codec.UTF8).getLines() map interpreter
        val os = new BufferedWriter(new FileWriter(outFile))


        res.foreach {l => os.write(l + "\n")}
        os.flush()
      }
      case _ => println("no match" + args.fold("") (_ + _))
    }
  }
}

```

This code does not use standard lib calendars or any other kind of calendar. As far as I can tell so far, it's completely accurate, but calendars are tough so it may not be.

This challenge was tough for many reasons, but the day of the gregorian new year in the french republican calendar changing 6 times in the past 200 years (and seemingly at random) didn't help.

My project takes DD/MM/YYYY for gregorian dates and the same format as in the op for French Revolutionary dates (though it also matches on roman numerals for the day and month field, no decade field specified with a 1-30 roman numeral for the day, 1-infinite whitespace between all words, optional accent aigu and accent circonflexe, etc.)

---

