# XFCE with i3wm
Configuration for use xfce4 with i3wm embedded.
![screen1](https://i.imgur.com/s3qnVq3.png)
![screen2](https://i.imgur.com/CMMjsnS.jpg)

## Configuration steps
1. Install iw3 from a xfce enviroment: 
  `yay -S i3-wm `
2. Modify config files to disable session saving, load i3 as WM and disable xfdesktop
  Replace the content of the file `~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml` with this:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<channel name="xfce4-session" version="1.0">
  <property name="general" type="empty">
    <property name="FailsafeSessionName" type="string" value="Failsafe"/>
    <property name="LockCommand" type="string" value=""/>
    <property name="SessionName" type="string" value="Default"/>
    <!-- disable session saving -->
    <property name="SaveOnExit" type="bool" value="false"/>
  </property>
  <property name="sessions" type="empty">
    <property name="Failsafe" type="empty">
      <property name="IsFailsafe" type="bool" value="true"/>
      <property name="Count" type="int" value="5"/>
      <property name="Client0_Command" type="array">
        <!-- use i3 as WM -->
        <value type="string" value="i3"/>
      </property>
      <property name="Client0_Priority" type="int" value="15"/>
      <property name="Client0_PerScreen" type="bool" value="false"/>
      <property name="Client1_Command" type="array">
        <value type="string" value="xfsettingsd"/>
      </property>
      <property name="Client1_Priority" type="int" value="20"/>
      <property name="Client1_PerScreen" type="bool" value="false"/>
      <property name="Client2_Command" type="array">
        <value type="string" value="xfce4-panel"/>
      </property>
      <property name="Client2_Priority" type="int" value="25"/>
      <property name="Client2_PerScreen" type="bool" value="false"/>
      <property name="Client3_Command" type="array">
        <value type="string" value="Thunar"/>
        <value type="string" value="--daemon"/>
      </property>
      <property name="Client3_Priority" type="int" value="30"/>
      <property name="Client3_PerScreen" type="bool" value="false"/>
      <property name="Client4_Command" type="array">
        <!-- empty value, we wont xfdesktop to start -->
        <value type="string" value=""/>
      </property>
      <property name="Client4_Priority" type="int" value="35"/>
      <property name="Client4_PerScreen" type="bool" value="false"/>
    </property>
  </property>
</channel>
```
3. kill cache & reboot
    * `rm -rf ~/.cache/*`
    * Reboot
4. Setup the shortcuts. </br>
  ![shortcuts](https://i.imgur.com/Vgn9iiI.png)
