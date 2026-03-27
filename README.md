# TenderEyes Workflow Engine

A full-stack business process workflow engine with a visual flowchart designer, built with Node.js, Express, MySQL, and vanilla JavaScript.

## 🎯 Features

- **Visual Workflow Designer** - Drag-and-drop interface powered by [@alyssaxuu/flowy](https://github.com/alyssaxuu/flowy)
- **Node Types** - Start, End, Task, Wait, Condition
- **Workflow Execution** - Execute workflows with async/await support
- **Execution Tracking** - Monitor workflow runs and view execution history
- **MySQL Database** - Persistent storage for workflows and executions
- **RESTful API** - Complete API for workflow management and execution
- **Responsive UI** - Works on desktop and tablet devices

## 🚀 Quick Start

### Prerequisites
- Node.js 14+
- MySQL 5.7+
- npm

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/tendereyesdevelop/TenderEyesWorkflow.git
   cd TenderEyesWorkflow
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Setup MySQL Database**
   ```bash
   mysql -u root -p < database/schema.sql
   ```

4. **Configure environment variables**
   ```bash
   cp .env.example .env
   ```
   Edit `.env` with your database credentials:
   ```
   DB_HOST=localhost
   DB_PORT=3306
   DB_USER=root
   DB_PASSWORD=your_password
   DB_NAME=tendereyes_workflow
   PORT=3000
   ```

5. **Start the server**
   ```bash
   npm run dev
   ```

6. **Open in browser**
   ```
   http://localhost:3000
   ```

## 📁 Project Structure

```
TenderEyesWorkflow/
├── public/
│   ├── index.html           # Main application HTML
│   ├── css/
│   │   └── styles.css       # Styling
│   └── js/
│       ├── app.js           # Main application logic
│       ├── api.js           # API client
│       └── designer.js      # Flowy designer controller
├── routes/
│   ├── workflows.js         # Workflow CRUD routes
│   └── executions.js        # Execution routes
├── engine/
│   └── WorkflowEngine.js    # Core workflow execution engine
├── database/
│   ├── schema.sql           # MySQL schema
│   └── connection.js        # Database connection pool
├── server.js                # Express server setup
├── package.json
├── .env.example
└── README.md
```

## 🔧 API Endpoints

### Workflows
- `GET /api/workflows` - Get all workflows
- `GET /api/workflows/:id` - Get specific workflow
- `POST /api/workflows` - Create new workflow
- `PUT /api/workflows/:id` - Update workflow
- `DELETE /api/workflows/:id` - Delete workflow

### Executions
- `GET /api/executions/workflow/:workflowId` - Get workflow executions
- `GET /api/executions/:id` - Get execution details
- `POST /api/executions/execute/:workflowId` - Execute workflow

## 📊 Database Schema

### workflows table
- `id` - Unique identifier (UUID)
- `name` - Workflow name
- `description` - Workflow description
- `status` - draft, published, or archived
- `definition` - JSON workflow definition with blocks and connections
- `created_at` - Creation timestamp
- `updated_at` - Last update timestamp

### executions table
- `id` - Unique execution identifier
- `workflow_id` - Reference to workflow
- `status` - pending, running, completed, failed, paused
- `input_data` - JSON input data
- `output_data` - JSON output data
- `error_message` - Error message if failed
- `started_at` - Execution start time
- `completed_at` - Execution completion time

### execution_history table
- Records individual node executions within a workflow run
- Tracks start, completion, and any errors per node

## 🎨 Node Types

### Start Node
- Workflow entry point
- No additional configuration

### End Node
- Workflow exit point
- No additional configuration

### Task Node
- Performs work/action
- Configurable name and description

### Wait Node
- Pauses execution for specified duration
- Configurable duration in milliseconds

### Condition Node
- Branches workflow based on condition
- Supports JavaScript expressions

## 📝 Example Workflow

1. Create a new workflow via the UI
2. Drag nodes from the palette to canvas
3. Connect nodes by snapping them together
4. Configure node properties in the right panel
5. Save the workflow
6. Execute via the "Execute" button
7. Monitor execution in the Executions section

## 🛠️ Development

### Run in development mode
```bash
npm run dev
```

### Run tests
```bash
npm test
```

## 📦 Dependencies

- **express** - Web framework
- **mysql2** - MySQL database driver
- **body-parser** - Request body parsing
- **dotenv** - Environment variables
- **cors** - CORS middleware
- **uuid** - ID generation
- **@alyssaxuu/flowy** - Flowchart designer

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Support

For issues and questions, please create an issue on the GitHub repository.

## 🚀 Future Enhancements

- [ ] Advanced node types (Loop, Parallel, SubWorkflow)
- [ ] Workflow versioning
- [ ] User authentication & authorization
- [ ] Workflow templates
- [ ] Real-time execution monitoring via WebSockets
- [ ] Workflow scheduling/cron support
- [ ] Data validation and transformation nodes
- [ ] Integration with external services (webhooks, APIs)