    def load_tasks():
    try:
        with open("tasks.txt", "r") as f:
            return [line.strip() for line in f.readlines()]
    except FileNotFoundError:
        return []

    def save_tasks(tasks):
    with open("tasks.txt", "w") as f:
        for task in tasks:
            f.write(task + "\n")

    def main():
    tasks = load_tasks()
    while True:
        print("\n1. View Tasks\n2. Add Task\n3. Delete Task\n4. Exit")
        choice = input("Choose an option: ")

        if choice == "1":
            for idx, task in enumerate(tasks, 1):
                print(f"{idx}. {task}")
        elif choice == "2":
            new_task = input("Enter task: ")
            tasks.append(new_task)
            save_tasks(tasks)
        elif choice == "3":
            for idx, task in enumerate(tasks, 1):
                print(f"{idx}. {task}")
            try:
                del_index = int(input("Enter task number to delete: ")) - 1
                if 0 <= del_index < len(tasks):
                    tasks.pop(del_index)
                    save_tasks(tasks)
                else:
                    print("Invalid task number.")
            except ValueError:
                print("Please enter a number.")
        elif choice == "4":
            break
        else:
            print("Invalid option.")

if __name__ == "__main__":
    main()
