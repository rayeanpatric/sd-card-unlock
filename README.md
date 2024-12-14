# 🔒 Removing SD Card Protection using `sdtool`  

> Free your SD card from write-protection dungeon.  

---

## 🤔 What’s This?  

Ever tried saving something to your SD card, only to get slapped with "write-protected" errors? Yeah, it’s annoying. But fear not! This guide walks you through **removing write protection** from your SD card using the magical `sdtool` on Linux.  

**No hacking, no drama—just freedom in a few steps.**  

---

## 🛠️ What You’ll Need  

Here’s your SD card liberation toolkit:  
- **MicroSD to SD adapter** – How else will your SD card talk to your computer?  
- **Laptop/PC with an SD card slot** – Because SD cards can’t plug into the cloud (yet).  
- **Manjaro Linux Live USB** – A bootable Linux system. (Don’t worry, I’ll guide you through it!)  

---

## 🐧 The Step-by-Step Guide  

### 1⃣ Step 1: **Prepare the Manjaro Live USB**  
1. Download [Manjaro Linux](https://manjaro.org/download/).  
2. Use a tool like [BalenaEtcher](https://etcher.balena.io/) or [Rufus](https://rufus.ie/) to create a bootable USB drive.  
3. Boot your computer into the Manjaro Live environment. (You’ll need to restart and hit a key like `F12` or `Esc` during boot to select the USB drive. Google your laptop model if you’re unsure.)  

---

### 2⃣ Step 2: **Install `sdtool` in Manjaro**  
Once you’re in the Manjaro Live system:  
1. Open the terminal.  
2. Install `yay`, a helper for installing apps:  
   ```bash  
   sudo pacman -S yay  
   ```  
3. Install `sdtool` using `yay`:  
   ```bash  
   yay -S sdtool  
   ```  

---

### 3⃣ Step 3: **Find Your SD Card**  
Now let’s identify your SD card:  
1. Insert your SD card into the card slot.  
2. Run this command to list all connected storage devices:  
   ```bash  
   lsblk  
   ```  
3. Look for your SD card in the list. It will look something like `mmcblk0`.  

---

### 4⃣ Step 4: **Unmount the SD Card**  
Before we do anything, unmount the SD card so it’s not actively used by the system:  
```bash  
sudo umount /dev/mmcblk0p*  
```  
(*Replace `0` with the actual number if your SD card device is different.*)  

---

### 5⃣ Step 5: **Check the Write Protection Status**  
Time to see what’s up with your SD card:  
```bash  
sudo sdtool /dev/mmcblk0 status  
```  
- If it says **"Temporary"**: You’re in luck!  
- If it says **"Permanent"**: Sorry, this guide can’t help with permanently locked cards.  

---

### 6⃣ Step 6: **Disable Write Protection**  
Here’s the big moment:  
```bash  
sudo sdtool /dev/mmcblk0 unlock  
```  
After running this, check the status again:  
```bash  
sudo sdtool /dev/mmcblk0 status  
```  
It should now say **"Off"**. If so, congratulations! Your SD card is no longer write-protected. 🎉  

---

### 7⃣ Step 7: **Done!**  
You’re all set! Now you can use your SD card like any other normal storage device. Move files, delete stuff, and live your best tech life.  

---

## 🖋️ Notes for Beginners  

- **What if I use Windows?**  
  You can still follow this guide by booting into the Manjaro Live USB environment. Linux doesn’t bite, I promise.  

- **Still stuck?**  
  Check out the official `sdtool` [GitHub repository](https://github.com/BertoldVdb/sdtool) for more advanced troubleshooting.  

---

## 💡 Why This Repo?  

This repo exists to save people from the tyranny of write-protected SD cards. Whether you’re a student struggling with SD card restrictions or just someone who loves solving tech problems, this guide is for you.  

---

### 🌟 A Final Thought  
*"Freedom is the right of all... SD cards."* - Optimus Prime, probably.  

Feel free to reach out if you have any issues or want to share your SD card liberation story. 🚀
