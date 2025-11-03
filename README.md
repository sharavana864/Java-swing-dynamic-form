# Dynamic Resizing Form (Java Swing)

### 🎯 **Aim**
To create a Java Swing form that **resizes dynamically** and **maintains alignment** of its components using the `GridBagLayout` manager.


### ⚙️ **Algorithm / Approach**
1. Create a `JFrame` and set its layout as `GridBagLayout`.
2. Define `GridBagConstraints` for positioning and resizing of components.
3. Add labels, text fields, and buttons with appropriate grid positions.
4. Assign `weightx`, `weighty`, and `fill` to ensure components expand with the window.
5. Pack the frame, set minimum size, and make it visible.


🧩 Output / Expected Result

A responsive User Registration Form appears.

Components remain aligned when resizing the window.

The Address text area expands vertically.

Buttons are centered at the bottom.


### 💻 **Program (DynamicForm.java)**

```java


import javax.swing.*;
import java.awt.*;

/**
 * DynamicForm.java
 * Demonstrates a Swing form that resizes dynamically and maintains alignment,
 * using GridBagLayout.
 */
public class DynamicForm extends JFrame {

    public DynamicForm() {
        super("Dynamic Resizing Form - GridBagLayout Example");
        initUI();
    }

    private void initUI() {
        JPanel content = new JPanel(new GridBagLayout());
        GridBagConstraints gbc = new GridBagConstraints();
        gbc.insets = new Insets(8, 8, 8, 8);

        JLabel title = new JLabel("<html><h2>User Registration</h2></html>");
        gbc.gridx = 0; gbc.gridy = 0; gbc.gridwidth = 2;
        gbc.anchor = GridBagConstraints.CENTER;
        gbc.fill = GridBagConstraints.HORIZONTAL;
        gbc.weightx = 1.0;
        content.add(title, gbc);

        gbc.gridwidth = 1;

        gbc.gridy = 1; gbc.gridx = 0; gbc.anchor = GridBagConstraints.EAST;
        content.add(new JLabel("Name:"), gbc);
        gbc.gridx = 1; gbc.fill = GridBagConstraints.HORIZONTAL; gbc.weightx = 1.0;
        content.add(new JTextField(20), gbc);

        gbc.gridy = 2; gbc.gridx = 0; gbc.anchor = GridBagConstraints.EAST;
        content.add(new JLabel("Email:"), gbc);
        gbc.gridx = 1; gbc.fill = GridBagConstraints.HORIZONTAL;
        content.add(new JTextField(20), gbc);

        gbc.gridy = 3; gbc.gridx = 0;
        content.add(new JLabel("Phone:"), gbc);
        gbc.gridx = 1; gbc.fill = GridBagConstraints.HORIZONTAL;
        content.add(new JTextField(15), gbc);

        gbc.gridy = 4; gbc.gridx = 0; gbc.anchor = GridBagConstraints.NORTHEAST;
        content.add(new JLabel("Address:"), gbc);
        gbc.gridx = 1; gbc.fill = GridBagConstraints.BOTH; gbc.weighty = 1.0;
        JScrollPane area = new JScrollPane(new JTextArea(5, 20));
        content.add(area, gbc);

        gbc.gridy = 5; gbc.gridx = 0; gbc.gridwidth = 2; gbc.weighty = 0;
        gbc.anchor = GridBagConstraints.CENTER;
        JPanel btnPanel = new JPanel(new FlowLayout());
        btnPanel.add(new JButton("Submit"));
        btnPanel.add(new JButton("Clear"));
        btnPanel.add(new JButton("Cancel"));
        content.add(btnPanel, gbc);

        setContentPane(content);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setMinimumSize(new Dimension(420, 360));
        setLocationRelativeTo(null);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            DynamicForm f = new DynamicForm();
            f.pack();
            f.setVisible(true);
        });
```

![Program Output](./1.png)
![Program Output](./2.png)
![Program Output](./3.png)
![Program Output](./4.png)
