---
title: "Programming Poker Timer With C and GTK+"
date: 2009-04-23
forum: Programming Talk
---

### Post by kike_coello on 2009-04-23
Hi all, I'm programming a poker timer and I am new. I'm teaching myself GTK+ using "Beginning Linux Programming" from Matthews and Stones and Krause's "Foundations of GTK Development".

I am getting a segmentation fault when I initialize my GtkBoxes. I can't see what's wrong with them. It seem to work on a previous version of my code, but now I've added frames to my program and don't see how that affects the boxes.

This is what I have so far: 

```

#include <gtk/gtk.h>
#include <stdio.h>

void closeApp(GtkWidget *window, gpointer data)
{
  gtk_main_quit();
}

int main(int argc, char *argv[])
{
  GtkWidget *window;
  GtkWidget *hbox1, *hbox2, *hbox3, *hbox4;
  GtkWidget *vbox1, *vbox2, *vbox3, *vbox4, *vbox5, *vbox6, *vbox7;
  GtkWidget *button_time, *button_start, *button_rewind, *button_forward;
  GtkWidget *label_sb_title, *label_bb_title, *label_ante_title;
  GtkWidget *label_sb, *label_bb, *label_ante;
  GtkWidget *label_game_type, *label_blind_profile;
  GtkWidget *combo_game_type, *combo_blind_profile;
  GtkWidget *frame_round, *frame_time_remaining, *frame_settings, *frame_buttons;

  gtk_init (&argc, &argv);
  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_window_set_title(GTK_WINDOW(window), "Poker Timer");
  gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
  gtk_window_set_default_size(GTK_WINDOW(window), 300, 500);
  g_signal_connect(GTK_OBJECT (window), "destroy", GTK_SIGNAL_FUNC (closeApp), NULL);

  button_start = gtk_button_new_with_label("Start Timer");
  button_time = gtk_button_new_with_label("00:00");
  button_rewind = gtk_button_new_with_label("Rewind 1 Blind");
  button_forward = gtk_button_new_with_label("Forward 1 Blind");

  label_sb_title = gtk_label_new("Small Blind");
  label_bb_title = gtk_label_new("Big Blind");
  label_ante_title = gtk_label_new("Ante");
  label_sb = gtk_label_new("25");
  label_bb = gtk_label_new("50");
  label_ante = gtk_label_new("0");
  label_game_type = gtk_label_new("Game Type");
  label_blind_profile = gtk_label_new("Blind Profiles");

  combo_game_type = gtk_combo_box_new_text();
  gtk_combo_box_append_text(GTK_COMBO_BOX(combo_game_type), "Tournament");
  gtk_combo_box_append_text(GTK_COMBO_BOX(combo_game_type), "Cash - Coins");
  gtk_combo_box_append_text(GTK_COMBO_BOX(combo_game_type), "Cash - Bills");

  combo_blind_profile = gtk_combo_box_new_text();
  gtk_combo_box_append_text(GTK_COMBO_BOX(combo_blind_profile), "Tournament: 25 / 50");
  gtk_combo_box_append_text(GTK_COMBO_BOX(combo_blind_profile), "Cash: $0.01 / $0.02");
  gtk_combo_box_append_text(GTK_COMBO_BOX(combo_blind_profile), "Cash: $1.00 / $2.00");

  frame_round = gtk_frame_new("Round: 1");
  frame_time_remaining = gtk_frame_new("Time Remaining");
  frame_settings = gtk_frame_new("Settings");
 
  gtk_frame_set_shadow_type(GTK_FRAME(frame_round), GTK_SHADOW_IN);
  gtk_frame_set_shadow_type(GTK_FRAME(frame_time_remaining), GTK_SHADOW_OUT);
  gtk_frame_set_shadow_type(GTK_FRAME(frame_settings), GTK_SHADOW_IN);
  gtk_frame_set_shadow_type(GTK_FRAME(frame_buttons), GTK_SHADOW_IN);

  vbox1 = gtk_vbox_new(TRUE, 10);
  vbox2 = gtk_vbox_new(TRUE, 10);
  vbox3 = gtk_vbox_new(TRUE, 10);
  vbox4 = gtk_vbox_new(TRUE, 10);
  vbox5 = gtk_vbox_new(TRUE, 10);
  vbox6 = gtk_vbox_new(TRUE, 10);
  vbox7 = gtk_vbox_new(TRUE, 10);
 
  hbox1 = gtk_hbox_new(TRUE, 10);
  hbox2 = gtk_hbox_new(TRUE, 10);
  hbox3 = gtk_hbox_new(TRUE, 10);
  hbox4 = gtk_hbox_new(TRUE, 10);
 
  gtk_box_pack_start(GTK_BOX(vbox1), label_sb_title, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(vbox1), label_sb, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(vbox2), label_bb_title, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(vbox2), label_bb, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(vbox3), label_ante_title, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(vbox3), label_ante, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(hbox1), vbox1, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(hbox1), vbox2, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(hbox1), vbox3, TRUE, FALSE, 10);
  gtk_container_add(GTK_CONTAINER(frame_round), hbox1);

  gtk_box_pack_start(GTK_BOX(hbox2), button_time, TRUE, TRUE, 10);
  gtk_container_add(GTK_CONTAINER(frame_time_remaining), hbox2);

  gtk_box_pack_start(GTK_BOX(vbox4), label_game_type, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(vbox4), label_blind_profile, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(vbox5), combo_game_type, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(vbox5), combo_blind_profile, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(hbox3), vbox4, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(hbox3), vbox5, TRUE, FALSE, 10);
  gtk_container_add(GTK_CONTAINER(frame_settings), hbox3);
 
  gtk_box_pack_start(GTK_BOX(hbox4), button_start, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(hbox4), button_rewind, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(hbox4), button_forward, TRUE, FALSE, 10);
  gtk_container_add(GTK_CONTAINER(frame_buttons), hbox4);
 
  gtk_box_pack_start(GTK_BOX(vbox7), frame_round, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(vbox7), frame_time_remaining, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(vbox7), frame_settings, TRUE, FALSE, 10);
  gtk_box_pack_start(GTK_BOX(vbox7), frame_buttons, TRUE, FALSE, 10);
  gtk_container_add(GTK_CONTAINER(window), vbox7);
  gtk_widget_show_all(window);
  gtk_main ();
   
  return 0;
}

```

Apparently the problem is on line 62. There weren't any homework problems in my book so I decided to do this as a personal project, anybody interested in finishing it with me or improving it is welcome. 

Thanks in advance.

---

### Post by kike_coello on 2009-04-23
Never mind,   the problem was before the box initialization, I had forgotten to initialize the last frame. Now my code works, and I'm going to start implementing the actions for the buttons and combo boxes.

---

