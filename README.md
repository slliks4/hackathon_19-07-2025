# What are we building

Just a folder structure that accepts nested folders that accepts notes

Folder -> {
    id: uuid,
    title: '',
    created_at: datetime,
    updated_at: datetime,
    dept: int,
    parent: uuid | null,
    notes: [{'id': uuid, 'title': str}],        # summary only
    subfolders: [{'id': uuid, 'title': str}],   # summary only
    is_trashed: bool,
    sort_index: int,
}

notes -> {
    id: uuid,
    title: '',
    content: '',
    created_at: datetime,
    updated_at: datetime,
    is_trashed: bool,
}

SubFolder -> folder
So the idea basically is creating a folder which can accept a list of subfolders and notes, by default it stores the uuid and title for easy fetching in the ui without having to get the full content of the folder or notes, only when expanded does it then do the full search

The dept just tells if it's nexted and how deep it is nexted,
starts from 0 - infinity (can't be infinite in practical)

Reason, if to avoid duplicate of names within the same dept.
