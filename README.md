from cProfile import label
import webbrowser
from logging import root
from msilib.schema import Font
from multiprocessing.sharedctypes import Value
import string
import pyttsx3
import tkinter
from tkinter.ttk import Button, Label
from unicodedata import name
import speech_recognition 
import pyautogui
import time
import os
import pywhatkit


root =tkinter.Tk()
save_sec = tkinter.StringVar()
root.title("VOICE ASSISTANT")
root.geometry('350x100')
root.configure(background="#ADD8E6")

#voice
voice = pyttsx3.init()
voices = voice.getProperty("voices")
voice.setProperty("voice",voices[1].id)

class new :
    def __init__(self,v):
        self.W = v
        
    def we(self):
        if self.W == "alt":
            pyautogui.keyDown("alt")
        elif self.W=="relese alt":
             pyautogui.keyUp("alt")
        elif self.W== "shift":
            pyautogui.press("shift")
        elif self.W == "relese shift":
            pyautogui.press("shift")    
        elif self.W == "space":
            pyautogui.press("space")
        elif self.W == "save":
            pyautogui.hotkey('ctrl','s')
        elif self.W == "copy":
            pyautogui.hotkey('ctrl','c')
        elif self.W == "past":
            pyautogui.hotkey('ctrl','v')
        elif self.W == "cut":
            pyautogui.hotkey('ctrl','x')
        elif self.W in"computer":
            pyautogui.hotkey('win','e')
        elif self.W in "new":
            pyautogui.hotkey('ctrl','n')
        elif self.W == "shutdown":
            os.system('shutdown /s /t 1')
        elif self.W == "restart":
            os.system('shutdown /r /t 1')    
        elif self.W in "save as"  :
            pyautogui.hotkey('ctrl','shift','s') 
        elif self.W in "Windows":
            pyautogui.press("win")
        elif self.W in "enter":
            pyautogui.press("enter")
        
        elif self.W in "Google":
            webbrowser.open("www.google.com")
            recognizer = speech_recognition.Recognizer()

            with speech_recognition.Microphone() as mic:
                print("listenin")
                
                recognizer.adjust_for_ambient_noise(mic)
                audio = recognizer.listen(mic)
                val = recognizer.recognize_google(audio,language="en-US")
                print(val)
            pyautogui.write(val)    
            
        elif self.W in "YouTube":
            print("hi")
            voice.say("yyutube  video name ")
            voice.runAndWait()
            recognizer = speech_recognition.Recognizer()

            with speech_recognition.Microphone() as mic:
                print("listenin")
                
                recognizer.adjust_for_ambient_noise(mic)
                audio = recognizer.listen(mic)
                Val = recognizer.recognize_google(audio,language="en-US")
                print(Val)
                
                
            def youtube_v(value):
                pywhatkit.playonyt(value)
            youtube_v(Val)           
            
                            
def save ():
    
    while True :
        voice.say("auto save on ")
        voice.runAndWait()
        time.sleep(60)
    
        pyautogui.hotkey('ctrl','s')                                   
            
                    
            
def un(): 
                
                
        while True:
            recognizer = speech_recognition.Recognizer()

            with speech_recognition.Microphone() as mic:
                print("listening")
                
                recognizer.adjust_for_ambient_noise(mic)
                audio = recognizer.listen(mic)
                t = recognizer.recognize_google(audio,language="en-US")
                print(t)
                
                
                if speech_recognition.UnknownValueError:
                    print("something went wrong")

            
            o= new(t)
            o.we()
            
           
photo =tkinter.PhotoImage(file='icon.png')         
w=Label(root,text="VOICE ASSISTANT",font=('Helvetica',15 ,'bold'),background='#ADD8E6') 
w.grid(column=2,row=3)   
b = Button(root,text="Start",command=un)  
b.grid(column=3,row=3) 
r = Button(root,text="Quite",command=root.destroy) 
r.grid(column=3,row=6) 
root.iconphoto(False,photo)
#in_la = tkinter.Label(root,text="enter the sec")
#in_la.grid(column=0,row=0)
#nw = tkinter.Entry(root,textvariable= in_la)
#nw.grid(column=4, row=5)
save_tex =Label(root,text="AUTO SAVE",font=('Helvetica',15 ,'bold'),background='#ADD8E6')
save_tex.grid(column=2,row=4)
save_s = Button(root,text="Start", command=save) 
save_s.grid(column=3,row=4)        

root.mainloop()


              
