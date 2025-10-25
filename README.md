# Day4_smartstudentgradingsystem
The c program calculates a students percentage  and assigns a grade based on marks and attendance.it uses nested if-else logic to apply grading rules and handle special grace mark conditions
#include <stdio.h>
int main() {
    float m1, m2, m3, m4, m5, attendance;
    float total, percentage;
    char grade;
    char remarks[20];
    
    // Input marks and attendance
    printf("Enter marks in 5 subjects: ");
    scanf("%f %f %f %f %f", &m1, &m2, &m3, &m4, &m5);
    printf("Enter attendance percentage: ");
    scanf("%f", &attendance);

    // Calculate total percentage
    total = m1 + m2 + m3 + m4 + m5;
    percentage = total / 5;

    // Apply grading logic using nested if–else
    if (attendance < 75) {
        grade = 'F';
        sprintf(remarks, "Fail (Low Attendance)");
    } else {
        if (percentage >= 90) {
            grade = 'A';
            sprintf(remarks, "Excellent");
        } else if (percentage >= 80) {
            grade = 'A';
            sprintf(remarks, "Very Good");
        } else if (percentage >= 70) {
            grade = 'B';
            sprintf(remarks, "Good");
        } else if (percentage >= 60) {
            grade = 'C';
            sprintf(remarks, "Average");
        } else if (percentage >= 50) {
            grade = 'D';
            sprintf(remarks, "Pass");
        } else if (percentage >= 45 && percentage < 50) {
            // Grace marks condition
            if (attendance >= 90) {
                percentage += 5;
                if (percentage >= 50) {
                    grade = 'D';
                    sprintf(remarks, "Pass (Grace Marks Applied)");
                } else {
                    grade = 'F';
                    sprintf(remarks, "Fail");
                }
            } else {
                grade = 'F';
                sprintf(remarks, "Fail");
            }
        } else {
            grade = 'F';
            sprintf(remarks, "Fail");
        }
    }

    // Display final results
    printf("\nTotal Percentage: %.2f%%", percentage);
    printf("\nAttendance: %.0f%%", attendance);
    printf("\nFinal Grade: %c", grade);
    printf("\nRemarks: %s\n", remarks);

    return 0;
}
