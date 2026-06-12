---
title: "Keyboard input hacking in GTK (alternative to .net WndProc in Mono)"
date: 2008-07-13
forum: Programming Talk
---

### Post by true_friend on 2008-07-13
Hi
I am trying to create a custom widget based on gtk textview (the gtk# bindings for C#). The purpose is to enable writing my local language Urdu in textview instead of English. I am unable to find how can I hack the keyboard input before it appears on screen (so I change the key values like a to &#1575; and b to &#1576; etc). I am a beginner so plz suggest me it this regards. Obviously I want to do it in c# (mono has Gdk.Keyboard, Gdk.Keymap and some other such classes, but I am unable to figure out a way to get the pressed key's value and change it before it is passed to textview buffer). At last here is the example my friend done in system.windows.forms textbox.
```
using System;
using System.Drawing;
using System.Drawing.Design;
using System.Collections;
using System.ComponentModel;
using System.Windows.Forms;
using System.Windows.Forms.Design;


namespace UrduCtrl
{
	enum KeyboardStates
	{
		kbNormal=0,
		kbShift=1,
		kbCtrl=2,
		kbAltGr=3
	}

	public class UrduTextPropertyEditor: UITypeEditor
	{
//		public override object EditValue( 
//			System.ComponentModel.ITypeDescriptorContext context, 
//			System.IServiceProvider provider, object value) 
//		{ 
//			IWindowsFormsEditorService frmsvr = (IWindowsFormsEditorService)provider.GetService(typeof(IWindowsFormsEditorService));
//			if(frmsvr == null)
//				return null;
//
//			UrduTextPropertyEditorDlg dlg= new UrduTextPropertyEditorDlg();
//			dlg.EditedText = (string) value;
//
//			//dlg.ShowDialog();
//			frmsvr.ShowDialog(dlg);
//
//			return (string) dlg.EditedText;
//		}

//		public override object EditValue(ITypeDescriptorContext context, IServiceProvider provider, object value)
//		{
//			if (context!=null && provider!=null)
//			{
//				IWindowsFormsEditorService edSrv= (IWindowsFormsEditorService)provider.GetService(typeof(IWindowsFormsEditorService));
//				if (edSrv!=null)
//				{
//					UrduTextPropertyEditorDlg dialog= new UrduTextPropertyEditorDlg();
//					if (value is String)
//						dialog.EditedText= (string)value;	
//					if (edSrv.ShowDialog(dialog)==System.Windows.Forms.DialogResult.OK)
//						value= dialog.EditedText;
//					dialog.Dispose();
//					dialog= null;
//				}
//			}
//			return value;
//		}

		public override System.Drawing.Design.UITypeEditorEditStyle 
			GetEditStyle(System.ComponentModel.ITypeDescriptorContext context) 
		{ 
			// We will use a window for property editing. 
			return UITypeEditorEditStyle.Modal; 
		}

		public override bool GetPaintValueSupported( 
			System.ComponentModel.ITypeDescriptorContext context) 
		{ 
			// No special thumbnail will be shown for the grid. 
			return false; 
		} 
	}

	/// <summary>
	/// Summary description for Class1.
	/// </summary>
	[System.Security.Permissions.PermissionSet(System.Security.Permissions.SecurityAction.Demand, Name="FullTrust")]
	public class UrduTextBox: System.Windows.Forms.TextBox
	{
		private int WM_CHAR = 0x102;
		private int WM_KEYDOWN = 0x100;
		private int WM_KEYUP = 0x101;
		private bool m_bIsUrdu;
		private KeyboardStates kbState;
		private Hashtable UrduPhonetic;
		private char  charSingleQuote= Convert.ToChar(39);

		public UrduTextBox()
		{

			this.Font = new System.Drawing.Font("Urdu Naskh Asiatype", 12F, System.Drawing.FontStyle.Bold, System.Drawing.GraphicsUnit.Point, ((System.Byte)(178)));
			this.RightToLeft = System.Windows.Forms.RightToLeft.Yes;
			//this.TextAlign = System.Windows.Forms.HorizontalAlignment.Right;
			this.m_bIsUrdu= true;
			kbState= KeyboardStates.kbNormal;

			
			UrduPhonetic= new Hashtable();
			UrduPhonetic['a']=new Key(0x0627, 0x0622, 0x0623);
			UrduPhonetic['b']=new Key(0x0628, 0x0628);
			UrduPhonetic['c']=new Key(0x0686, 0x062B);
			UrduPhonetic['d']=new Key(0x062F, 0x0688);
			UrduPhonetic['e']=new Key(0x0639, 0x0651);
			UrduPhonetic['f']=new Key(0x0641, 0x64D);
			UrduPhonetic['g']=new Key(0x06AF, 0x063A);
			UrduPhonetic['h']=new Key(0x06BE, 0x062D);
			UrduPhonetic['i']=new Key(0x06CC, 0x0670);
			UrduPhonetic['j']=new Key(0x062C, 0x0636);
			UrduPhonetic['k']=new Key(0x06A9, 0x062E);
			UrduPhonetic['l']=new Key(0x0644, 0x0628);
			UrduPhonetic['m']=new Key(0x0645, 0x64B);
			UrduPhonetic['n']=new Key(0x0646, 0x06BA);
			UrduPhonetic['o']=new Key(0x06C1, 0x06C3);
			UrduPhonetic['p']=new Key(0x067E, 0x064F);
			UrduPhonetic['q']=new Key(0x0642);
			UrduPhonetic['r']=new Key(0x0631, 0x0691);
			UrduPhonetic['s']=new Key(0x0633 , 0x0635);
			UrduPhonetic['t']=new Key(0x062A , 0x0679);
			UrduPhonetic['u']=new Key(0x0626 , 0x0621);
			UrduPhonetic['v']=new Key(0x0637, 0x0638);
			UrduPhonetic['w']=new Key(0x0648, 0x0624);
			UrduPhonetic['x']=new Key(0x0634, 0x0698);
			UrduPhonetic['y']=new Key(0x06D2, 0x06D2);
			UrduPhonetic['z']=new Key(0x0632, 0x0630);
			UrduPhonetic['0']=new Key(0x0030, Convert.ToInt16(')'));
			UrduPhonetic['1']=new Key(0x0031, Convert.ToInt16('!'));
			UrduPhonetic['2']=new Key(0x0032, Convert.ToInt16('@'));
			UrduPhonetic['3']=new Key(0x0033, Convert.ToInt16('#'));
			UrduPhonetic['4']=new Key(0x0034, Convert.ToInt16('$'));
			UrduPhonetic['5']=new Key(0x0035, Convert.ToInt16('%'));
			UrduPhonetic['6']=new Key(0x0036, Convert.ToInt16('^'));
			UrduPhonetic['7']=new Key(0x0037, Convert.ToInt16('&'));
			UrduPhonetic['8']=new Key(0x0038, Convert.ToInt16('*'));
			UrduPhonetic['9']=new Key(0x0039, Convert.ToInt16('('));
			UrduPhonetic['=']=new Key(0x03D, 0x02B);
			UrduPhonetic['-']=new Key(0x002D, 0x0640);
			UrduPhonetic[',']=new Key(0x060C, 0x064E);
			UrduPhonetic['.']=new Key(0x06D4, 0x0650);
			UrduPhonetic['/']=new Key(0x002F, 0x061F);
			UrduPhonetic['\\']=new Key(0x0674);
			UrduPhonetic[';']=new Key(0x061B, 58);
			UrduPhonetic['[']=new Key(0x64C);
			UrduPhonetic[']']=new Key(0x0652);
			UrduPhonetic[charSingleQuote]=new Key(0x2018, 0x201C);
			UrduPhonetic['~']=new Key(0x2019, 0x201D);
			UrduPhonetic[' ']=new Key(32, 0x200C);
			UrduPhonetic['<']=new Key(0x064E);


		}

		protected override void WndProc(ref Message m)
		{			
			if (m.Msg == WM_CHAR)
			{				
				if(kbState== KeyboardStates.kbCtrl)
				{
					if(m.WParam == (IntPtr) 32)
					{
						this.m_bIsUrdu= !(this.m_bIsUrdu);
						m.WParam= (IntPtr) 0;
						base.WndProc(ref m);
						return;
					}
				}

				if(m_bIsUrdu)
				{
					//MessageBox.Show("Test");
					char strChar= (char) m.WParam;
					strChar= Char.ToLower(strChar);

					if (kbState== KeyboardStates.kbShift)
					{
						if (UrduPhonetic.ContainsKey(strChar))
						{
							m.WParam= (IntPtr) ((UrduCtrl.Key) UrduPhonetic[strChar]).shift;
						}
					}
					else if (kbState== KeyboardStates.kbAltGr)
					{
						if (UrduPhonetic.ContainsKey(strChar))
						{
							m.WParam= (IntPtr) ((UrduCtrl.Key) UrduPhonetic[strChar]).altgr;
						}
					}
					else if (kbState== KeyboardStates.kbNormal)
					{
						if (UrduPhonetic.ContainsKey(strChar))
						{
							m.WParam= (IntPtr) ((UrduCtrl.Key) UrduPhonetic[strChar]).normal;
						}
					}
				}			
			}
			else if (m.Msg == WM_KEYDOWN)
			{				
				if((Control.ModifierKeys & Keys.Shift) == Keys.Shift )
				{
					this.kbState= KeyboardStates.kbShift;
				}
				else if(((Control.ModifierKeys & Keys.Control) == Keys.Control) && (((Control.ModifierKeys & Keys.Alt) == Keys.Alt)))
				{
					this.kbState= KeyboardStates.kbAltGr;
					char strChar= (char) m.WParam;
					strChar= Char.ToLower(strChar);
				}
				else if((Control.ModifierKeys & Keys.Control) == Keys.Control )
				{
					this.kbState= KeyboardStates.kbCtrl;
				}
			}
			else if (m.Msg == WM_KEYUP)
			{		
				if(kbState == KeyboardStates.kbAltGr)
				{
					if(!(((Control.ModifierKeys & Keys.Control) == Keys.Control) && (((Control.ModifierKeys & Keys.Alt) == Keys.Alt))))
					{
						this.kbState= KeyboardStates.kbNormal;
					}
				}
				else if(kbState == KeyboardStates.kbCtrl)
				{
					if((Control.ModifierKeys & Keys.Control) != Keys.Control )
					{
						this.kbState= KeyboardStates.kbNormal;
					}
				}
				else if(kbState == KeyboardStates.kbShift)
				{
					if((Control.ModifierKeys & Keys.Shift) != Keys.Shift)
					{
						this.kbState= KeyboardStates.kbNormal;
					}
				}
			}
			base.WndProc(ref m);
		}

		
		[Category("Appearance"), 
		Description("Text property for Urdu edit control."), 
		Editor(typeof(UrduTextPropertyEditor), typeof(UITypeEditor))]
		public override string Text
		{
			get
			{
				return(base.Text);
			}
			set
			{
				base.Text = value;
				this.Invalidate();
			}
		}
	}
}

```
Regards

---

### Post by true_friend on 2008-07-14
I've tried documentation and able to get values of modifier keys like Alt, Ctrl, Windows key etc. It is achieved by a keypress event handler in c# but I am still unable to grab the input of normal typing keys A,a,B,b etc. The do not return a value :S. 
So this code shows the value of modifier keys only in textview at cursor.
> protected virtual void OnEventbox1KeyPressEvent (object o, Gtk.KeyPressEventArgs args)
	{
		textview1.Buffer.InsertAtCursor(args.Event.Key.ToString());
	}
While typing keys are typed as is. As far as I could understand the WndProc method in winforms which is overridden in above code should have an equivalent in gtk. If someone can suggest what is the equivalent?
Regards

---

### Post by true_friend on 2008-07-15
At last I've found a solution to get events from normal keys as well by adding [GLib.ConnectBefore] attribute before the event handler method.

---

### Post by Moriator on 2008-10-01
@true_friend: can you explain your solution more clearly? I can't do it. Thanks!

---

