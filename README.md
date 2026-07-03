[![LiaScript](https://raw.githubusercontent.com/LiaScript/LiaScript/master/badges/course.svg)](https://liascript.github.io/course/?https://raw.githubusercontent.com/tristantautenhahn/Englisch_Projekt_2026/main/README.md)


# Arduino Alvik
![Arduino Alvik](https://raw.githubusercontent.com/tristantautenhahn/Englisch_Projekt_2026/main/alvik.jpg)


# Goal for the robot
- robot that can detect obstacles and can avoid them
- detecting on wich side the obstacle is
- considered to map the surroundings

# Problems with (lack of) version control
- no Github
- online codeshare
- one member had to compile

# Deadlock
- kept getting stuck
- lights to debug on the side of the obstacle
- froze when rotated left-center
- sometimes froze when rotating away from center in different direction

# Code Snippet
```c++
switch (obstacle_index)
{
  case LEFT:
    alvik.left_led.set_color(1, 0, 0);
    alvik.right_led.set_color(0, 0, 0);
    Serial.print("rotating left by ");
    Serial.print(-angle_increment);
    rotate(-angle_increment);    // 'rotate(...)' instead of 'alvik.rotate(...)'
    break;
  case LEFT_CENTER:
    alvik.left_led.set_color(1, 1, 0); 
    alvik.right_led.set_color(0, 0, 0);
    Serial.print("rotating left center by ");
    Serial.print(-2.0 * angle_increment);
    rotate(-2.0 * angle_increment);
    break;
  case CENTER:
    alvik.left_led.set_color(0, 1, 0);
    alvik.right_led.set_color(0, 1, 0);
    Serial.print("rotating from center...");
    rotate_away();
    break;
  case RIGHT_CENTER:
    alvik.left_led.set_color(0, 0, 0);
    alvik.right_led.set_color(0, 1, 1);
    Serial.print("rotating right center by ");
    Serial.print(2.0 * angle_increment);
    rotate(2.0 * angle_increment);
    break;
  case RIGHT:
    alvik.left_led.set_color(0, 0, 0);
    alvik.right_led.set_color(0, 0, 1);
    Serial.print("rotating right by ");
    Serial.print(angle_increment);
    rotate(angle_increment);
    break;
}
```

```c++
/*
  Alternative to the built-in 'rotate' function.
  Tries to avoid deadlocks.
*/
inline void rotate(const float angle) {
  alvik.drive(0.0, angle);
  delay(1000);
  alvik.brake();
}
```

# Padlet posts
- we uploaded updates to the Padlet
- we explained the Time-of-Flight sensor of the Alvik
- the French showed their robot

# Reflection
- **use version control in the future**
- improve communication with the French

# Conclusion
- it was fun
- problems were challenging, but part of the process
- enjoyable experience overall
