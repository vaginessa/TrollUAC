# TrollUAC
- .NET library that serves as a UAC bypass for x64
- Any* process with the uiAccess flag enabled can "Send Keystrokes" to high integrity processes even from medium integrity
- We steal the token of On Screen Keyboard (uiAccess enabled) to spawn a new process that does GUI automation
- The GUI automation simply sends keystrokes to taskmgr (auto elevate) to spawn our new desired process in high integrity
-  *Refer to tiraniddo's article for requirements, although they can easily be conjured up 
![TrollUAC](https://github.com/cybersectroll/TrollUAC/assets/169176042/ffe843de-6d92-4508-9046-1cec850473ad)

  
# Why?
Because I was bored of registry / DLL / com UAC bypasses

# Benefits
The code really serves as boilerplate to abuse the uiAcess feature in convenient c# where you can easily replace the GUI automation code/logic to your liking

# Credits (rewrite of project) 
c# port of https://www.tiraniddo.dev/2019/02/accessing-access-tokens-for-uiaccess.html with some troll flavouring.\
Refer to article for full explanation, technique is 5 years old but still works :)
       
# Compiling  
- Download project & Compile solution as Release, x64, check the box "allow unsafe code"
- No external dependencies needed
 
# Usage 
```
> Start with Medium Integrity
> [System.Reflection.Assembly]::LoadFrom("C:\users\public\TrollUAC.dll")   //can Load() as well 
> [TrollUAC]::uiAccessPlease(<Process>)  //for non sys32 binaries, set full path
> [TrollUAC]::uiAccessPlease("notepad")
```

# OPSEC
- This project is declared 100% opsec unsafe

# Wishlist - Project was done over the weekend and I have no time/intent to pursue the following:
- none, i think it works fine in any non-production environment like security certification exams 
  
# Disclaimer
Should only be used for educational purposes!
