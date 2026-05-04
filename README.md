# tegede-highschool
import java.util.ArrayList;
import java.util.Scanner;

class Student {
    int id;
    String name;
    int grade;

    Student(int id, String name, int grade) {
        this.id = id;
        this.name = name;
        this.grade = grade;
    }

    void display() {
        System.out.println("ID: " + id + ", Name: " + name + ", Grade: " + grade);
    }
}

public class StudentManagementSystem {
    static ArrayList<Student> students = new ArrayList<>();
    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {
        int choice;

        do {
            System.out.println("\n--- TEGEDIE HIGH SCHOOL STUDENT SYSTEM ---");
            System.out.println("1. Add Student");
            System.out.println("2. View Students");
            System.out.println("3. Search Student");
            System.out.println("4. Delete Student");
            System.out.println("5. Exit");
            System.out.print("Enter choice: ");

            choice = sc.nextInt();

            switch (choice) {
                case 1:
                    addStudent();
                    break;
                case 2:
                    viewStudents();
                    break;
                case 3:
                    searchStudent();
                    break;
                case 4:
                    deleteStudent();
                    break;
                case 5:
                    System.out.println("Exiting...");
                    break;
                default:
                    System.out.println("Invalid choice!");
            }
        } while (choice != 5);
    }

    static void addStudent() {
        System.out.print("Enter ID: ");
        int id = sc.nextInt();
        sc.nextLine(); // clear buffer

        System.out.print("Enter Name: ");
        String name = sc.nextLine();

        System.out.print("Enter Grade: ");
        int grade = sc.nextInt();

        students.add(new Student(id, name, grade));
        System.out.println("Student added successfully!");
    }

    static void viewStudents() {
        if (students.isEmpty()) {
            System.out.println("No students found!");
        } else {
            for (Student s : students) {
                s.display();
            }
        }
    }

    static void searchStudent() {
        System.out.print("Enter ID to search: ");
        int id = sc.nextInt();

        for (Student s : students) {
            if (s.id == id) {
                s.display();
                return;
            }
        }
        System.out.println("Student not found!");
    }

    static void deleteStudent() {
        System.out.print("Enter ID to delete: ");
        int id = sc.nextInt();

        for (Student s : students) {
            if (s.id == id) {
                students.remove(s);
                System.out.println("Student deleted!");
                return;
            }
        }
        System.out.println("Student not found!");
    }
}