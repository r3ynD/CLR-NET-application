# CLR-NET-application
C++ CLR application for calculating the area and points of a figure with the calculation of the percentage error

<a href="https://www.ncfu.ru/export/uploads/imported-from-dle/op/doclinks2017/23_Metod_PnaYVUKPLR_11.03.02.pdf">Program guidelines (pages 54-57)</a>
Step-by-Step Guide
1. Identify the constituent parts of the figure's borders: from the figure in the image, it can be concluded that its border consists of three lines.

2. Determine the calculated area of the figure. From the image, it can be seen that it consists of two shapes: a semicircle with a radius of 100 and a rectangular triangle with legs of 100 and 200. Therefore, the total area of the figure is equal to: Sp = 10000π/2 + 10000.

3. Enter into the Visual Studio environment.

4. In the Create Project window, expand the Visual C++ node and navigate to the CLR option. Choose the Windows Form Application option from the central panel.

5. In the editor's Name field (which is initially labeled <Enter name>), enter the project’s name, Visual_Lab7. In the Location field, specify the location of the project or select the location using the Browse button (for example, N:\\CI\2_trim\Lab7).

6. Change the value of the Text property for the form, entering data such as "Performed by a student of the IT department group-121 Ivanov P.A., Task 7."

7. Place the Chart1 component on the form. Use the Anchor property to attach the component to all sides of the form. The Chart1 component should take up almost the entire form area, and will change its size accordingly when the form's size is changed. However, this is not the best way to adjust the graph's size to the form's size since there may be distortions of the figure's proportions in height and width. Alternatively, it is better to calculate the Chart1 component's size in the Resize event handler for the form and assign identical heights and widths based on the lowest available size in the client area (pre-determine which area other components occupy vertically or horizontally).

8. Place a series of components on the form (including 5 TextBox components, 5 Label components, 3 Button components, and 1 Chart component) to display the results (as shown in Fig.7.3). Use the Anchor property to attach components on the left to the form's left edge, while the components on the right should be attached to the right edge. Attach the "Figure", "Calculation", and "Exit" buttons to the lower edge. When the form's size is changed, it is better to recalculate the button's width, so they will increase proportionally while remaining "anchored" to the bottom edge of the form. The form should be approximately as shown in the image:
  
  At the design stage:
  
![image](https://github.com/r3ynD/CLR-NET-application/assets/127958857/fb66bb04-9311-4fb1-a8e9-d8576b7f2d15)
  
After the calculation:
  
![image](https://github.com/r3ynD/CLR-NET-application/assets/127958857/3a9f398c-7a70-440b-932d-99c4757b43fc)

9. To components TextBox2, TextBox3, TextBox4, and TextBox5, assign the value true to the ReadOnly property, preventing the user from entering any data into the component. For the component TextBox1, data will be entered from the keyboard using the component TextBox. Enter the value "10000" into the Text property of this component - the default value. This value will be displayed when the application is launched. In the course of application execution, it can be replaced with another value. 

10. Through the Series property of the Chart1 component, bring up the Series Collection Editor window. Add a Series to display the border of the figure (according to the number of constituent parts of the figure contour). In the original example, there are three charts. Choose Line or Spline as the chart type. Take the same color for all charts. Add two more Point-type Series to display random points (a total of five Series should be included for this example). Choose the color of these points at your discretion and set the Marker Size to 1. 

11. In the object code of the created project, add library connections: 
```
#pragma once #include
<cmath> #include
<stdlib.h> #include
<time.h>
#define _USE_MATH_DEFINES
#include <math.h>
```

12. Add the following line to the using section: 

`using namespace System::Windows::Forms::DataVisualization::Charting;`

13. Double-click the "Figure" button with the left mouse button, and the contour of the figure will be drawn in the Chart1 component. Each constituent part (three in total) is drawn into its own Series. When displayed, they touch each other, forming a single contour. Insert the following program code into the template code: 
```
Series^ plot1 = chart1->Series[0];
Series^ plot2 = chart1->Series[1];
Series^ plot3 = chart1->Series[2];
double y, x;
// Draw the top part of the figure - a semicircle with a radius of 100
for (int i=-100; i<=100; i++)
{ x=i; y=sqrt(10000-
x*x);
plot1->Points->AddXY(x, y);
}
// Draw the second part - the inclined line y=-0.5(x+100)
for (int i=-100; i<=100; i++)
{ x=i; y=-0.5*(x+100);
plot2->Points->AddXY(x, y);
}
// Draw the vertical line x=100.
for (int i=-100; i<=0; i++)
{x=100;
y=i; plot3->Points->AddXY(x,y);
}
 ```
  
  <h3>My result:</h3>
  
![image](https://github.com/r3ynD/CLR-NET-application/assets/127958857/5e955eaa-638c-4a7e-a836-fa1630d275cb)

<h3>Working program:</h3>

<img src="https://github.com/r3ynD/CLR-NET-application/assets/127958857/cd86b373-1d5c-4636-8a7a-1ce6cf8ec3f4" width=70%> 

