# Simple File Upload Service

A lightweight Node.js/Express backend for handling file uploads, storage, and retrieval.

## Installation

1.  Clone the repository or download the source code.
2.  Install dependencies:
    ```bash
    npm install
    ```

## Running the Server

### Development (Auto-restart)
```bash
npm run dev
```

### Production
Start the server using Node.js:

```bash
node server.js
```

The server will start on port **3000** by default.
Uploads will be stored in the `uploads/` directory.

## API Documentation

### 1. Upload a File

Upload a single file to the server.

-   **URL**: `/upload`
-   **Method**: `POST`
-   **Content-Type**: `multipart/form-data`
-   **Body Parameters**:
    -   `file`: The file object to upload.

**Success Response:**

-   **Code**: `201 CREATED`
-   **Content**:
    ```json
    {
      "message": "File uploaded successfully",
      "filename": "uuid-generated-name.jpg",
      "url": "http://localhost:3000/files/uuid-generated-name.jpg",
      "originalName": "my-image.jpg",
      "size": 102400,
      "mimetype": "image/jpeg"
    }
    ```

### 2. Get a File

Retrieve (download/view) a previously uploaded file.

-   **URL**: `/files/:filename`
-   **Method**: `GET`
-   **URL Params**:
    -   `filename`: The name of the file returned during upload.

**Example**: `http://localhost:3000/files/uuid-generated-name.jpg`

### 3. Delete a File

Remove a file from the server.

-   **URL**: `/files/:filename`
-   **Method**: `DELETE`
-   **URL Params**:
    -   `filename`: The name of the file to delete.

**Success Response:**

-   **Code**: `200 OK`
-   **Content**:
    ```json
    {
      "message": "File deleted successfully"
    }
    ```

**Error Response:**

-   **Code**: `404 NOT FOUND`
-   **Content**: `{ "error": "File not found" }`
