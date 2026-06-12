---
title: "Change defaults in &quot;top&quot; utility"
date: 2011-03-02
forum: Programming Talk
---

### Post by kunalgrao on 2011-03-02
Hi

 I have a system with multiple cores. I want to see the usage of each core. Top command allows me to see that but only in interactive mode. i.e. I start the "top" command and then press "1" so that it toggles the display to show all the cores. Top 
utility manual shows this:

 Summary_Area_defaults
              'l' - Load Avg/Uptime  On  (thus program name)
              't' - Task/Cpu states  On  (1+1 lines, see '1')
              'm' - Mem/Swap usage   On  (2 lines worth)
              '1' - Single Cpu       On  (thus 1 line if smp)

 So, for that last one, I want to change that default to "Off" ..so that as soon as I start "top" it shows me all the cores usage. I don't see a way to do it through command-line as well. 

The reason I want to do this is because, I want to send the output of top command (in batch mode) for 1 iteration to a file and then read that file in the program and check the usage of each CPU core. Let me know if there is a way to do that, else should I try to modify the top utility source code and change that default behaviour ?

Thanks & Regards,
Kunal

---

### Post by kunalgrao on 2011-03-04
Hi

  I modified the "top" utility source code slightly and got what I wanted..

Thanks & Regards,
Kunal

---

### Post by Vox754 on 2011-03-04
> **kunalgrao said:**
> Hi

  I modified the "top" utility source code slightly and got what I wanted..

Thanks & Regards,
Kunal

Post the changes made to the source code, perhaps a patch.

That way people in the distant future will look at your post with awe at how hacker you are.

Seriously, I hate when people start a thread, then say "fixed it", without providing the solution.

---

### Post by kunalgrao on 2011-03-16
Sorry for not providing the solution..well, it was not very difficult. Here is the modified source code 
(line 2986 in top.c):

 // Display Task and Cpu(s) States
   if (CHKw(Curwin, View_STATES)) {
      show_special(
         0,
         fmtmk(
            STATES_line1,
            Frame_maxtask, Frame_running, Frame_sleepin, Frame_stopped, Frame_zombied
         )
      );
      Msg_row += 1;

      smpcpu = cpus_refresh(smpcpu);

/*      if (CHKw(Curwin, View_CPUSUM)) {
         // display just the 1st /proc/stat line
         summaryhlp(&smpcpu[Cpu_tot], "Cpu(s):");
      } else {

*/       int i;
         char tmp[SMLBUFSIZ];
         // display each cpu's states separately
         for (i = 0; i < Cpu_tot; i++) {
            snprintf(tmp, sizeof(tmp), "Cpu%-3d:", smpcpu[i].id);
            summaryhlp(&smpcpu[i], tmp);
         }
         summaryhlp(&smpcpu[Cpu_tot], "Cpu(s):");
//      }
   }

Hope somebody will find this useful in future ..

Thanks & Regards,
Kunal

---

### Post by p0rkjello on 2011-03-16
Go into the interactive mode and set your preferences. The press W. This will write a config file to your home directory. Next time you start top it will display with your preferences.

- Enjoy

---

### Post by kunalgrao on 2011-03-17
wow ..This is great solution ..and it works ..just 1 thing missing is that when we start top and press 1, it shows individual cpu core utilization but not aggregate ..i would like to have the aggregate as well ..so will stick with what i have done ..but thanks a lot for pointing this solution with config file ..

---

